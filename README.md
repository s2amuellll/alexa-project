import speech_recognition as sr
import pyttsx3
import wikipedia
import datetime
import pyaudio


audio = sr.Recognizer()
maquina = pyttsx3.init()
maquina.say('Eu sou Pedro, Como posso ajudar')
maquina.runAndWait()

def executar_comando():
    try:
        with sr.Microphone() as source:
            print('Ouvindo...')
            voz = audio.listen(source)
            comando = audio.recognize_google(voz, language='pt-BR')
            comando = comando.lower()
            if 'pedro' in comando:
                comando = comando.replace('pedro','')
                print(comando)
                maquina.runAndWait()

    except:
        print('O microfone não esta funcionando')



def comando_voz():
    comando = executar_comando()
    if 'horas' in comando and comando ['horas']:
        hora = datetime.datetime.now().strftime('%H:%M')
        print(hora)
        maquina.say("agora são " + hora)
        maquina.runAndWait()
    elif 'procure por' in comando:
        procurar = comando.replace('procure por', '')
        wikipedia.set_lang('pt')
        wik = wikipedia.summary(procurar, 2)
        print(wik)
        maquina.say(wik)
        maquina.runAndWait()
        

while True:
    comando_voz()






this is the error
Traceback (most recent call last):
  File "/home/sam/python project/pyautogui/mandarmsg.py", line 47, in <module>
    comando_voz()
  File "/home/sam/python project/pyautogui/mandarmsg.py", line 32, in comando_voz
    if 'horas' in comando and comando ['horas']:
TypeError: argument of type 'NoneType' is not iterable
