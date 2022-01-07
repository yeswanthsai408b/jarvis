import pyttsx3 

import speech_recognition as sr 

import datetime

import wikipedia 

import os

import webbrowser

import pyautogui

import time

import smtplib

import pyjokes


engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
# print(voices[1].id)
engine.setProperty('voice', voices[0].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def wishMe():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good Morning!")

    elif hour>=12 and hour<18:
        speak("Good Afternoon!")   

    else:
        speak("Good Evening!")

    speak("Please tell me how may I help you")      

        


             

def takeCommand():
    #It takes microphone input from the user and returns string output

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")    
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")

    except Exception as e:
        # print(e)    
        print("Say that again please...")
        speak("say that again please")  
        return "None"
    return query




if __name__ == "__main__":
    wishMe()
    while True:
        query = takeCommand().lower()
        if 'wake up' in query:
            speak("i am back ,,,, plese tell me what can i do for you")
            speak("password approuved")


            while True:
        
                query = takeCommand().lower()
                # Logic for executing tasks based on query
                if 'wikipedia' in query:
                    speak('Searching Wikipedia...')
                    query = query.replace("wikipedia", "")
                    results = wikipedia.summary(query, sentences=2)
                    speak("According to Wikipedia")
                    print(results)
                    speak(results)
                elif 'open youtube' in query:
                    webbrowser.open("youtube.com")
                elif 'open google' in query:
                    webbrowser.open("google.com")
                elif 'type' in query:
                    newt = query.replace('type ','')
                    pyautogui.typewrite(newt)
                    speak("done!")
                elif 'are you there' in query:
                    speak("i am here")
                elif 'open code' in query:
                    speak("opened vs code")
                    codepath1="C:\\Users\\Anandhan\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
                    os.startfile(codepath1)
                elif 'OBS studio' in query:
                    speak("opening OBS studio")
                    codepath="C:\\Users\\Anandhan\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
                    os.startfile(codepath1)
                elif 'open microsoft browser' in query:
                    speak("opening edge")
                    codepath="C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe"
                    os.startfile(codepath)
                elif 'open flimora' in query:
                    speak("opening wondershare flimora")
                    codepath1="C:\\Program Files (x86)\\Wondershare\\Wondershare Filmora (CPC)\\Wondershare Filmora X.exe"
                    os.startfile(codepath1)
                elif 'open code2' in query:
                    speak("oppening pycharm")
                    codepath1="D:\\pycharm\\PyCharm Community Edition 2021.2.2\\bin"
                elif 'open unity hub' in query:
                    speak("opening unity hub")
                    codepath="D:\\unity\\unity hub\\Unity Hub.exe"
                    os.startfile(codepath)
                elif 'the time' in query:
                    strTime = datetime.datetime.now().strftime("%H:%M")    
                    speak(f"Sir, the time is {strTime}") 
                elif "joke" in query:
                    joke=pyjokes.get_joke(language='en', category= 'all')
                    print(joke)
                    speak(joke)
                       
                elif 'quit' in query:
                    speak("quitting sir")
                    break
                elif 'turn off' in query:
                    speak("powering off")
                    speak("S T R 1 power off S S 2 exit")
                    exit()
                elif 'shutdown' in query:
                    speak("okay")
                    os.system("shutdown /s /t 1")
                    speak("i am going to shutdown the laptop sir")
                    speak("bye , thank you")
                    speak("S T 1 shutdown jarvis shutoff main processor mother board")
