---
title: "amulegui crash when connects to the amuled if it is owned by other user"
date: 2016-09-05
forum: General Help
---

### Post by frisix on 2016-09-05
Hi.


I've installed **amuled** on a machine running ubuntu 16.06 64bits with a user created from the gui for that propose. 

Also I've used the **amule** program before for setting up the remote connections to the daemon and started **amule daemo**n.

Well, when I run the **amulegui** logged as the user amule the client works as expected but, when I run the **amulegui** from another user, the client crashes. I'm able to run the **amulecmd** client form the user but not the **amulegui**.

- Could you help me?


The versions that are installed are the following:


amule 2.4.0~git20151120.0023527bc2-1ubuntu1
amule-common 2.4.0~git20151120.0023527bc2-1ubuntu1
amule-daemon 2.4.0~git20151120.0023527bc2-1ubuntu1
amule-utils 2.4.0~git20151120.0023527bc2-1ubuntu1
amule-utils-gui 2.4.0~git20151120.0023527bc2-1ubuntu1

I set up this on ubuntu 14.04 64bits and it worked. 


This is the output when I run the amulegui from the terminal:

 2016-09-05 17:14:08 (remote-GUI): Initialising aMuleGUI SVN compiled with wxGTK2 v3.0.2 and Boost 1.58
 2016-09-05 17:14:08 (remote-GUI): Checking if there is an instance already running...
 2016-09-05 17:14:08 (remote-GUI): No other instances are running.
 2016-09-05 17:14:08 (remote-GUI): Asio thread 1 started
 2016-09-05 17:14:08 (remote-GUI): Asio thread 2 started
 2016-09-05 17:14:08 (remote-GUI): Asio thread 3 started
 2016-09-05 17:14:08 (remote-GUI): Asio thread 4 started
 2016-09-05 17:14:12 (remote-GUI): Conectando...
 2016-09-05 17:14:12 (remote-GUI): Entrando en bucle de eventos...
 2016-09-05 17:14:12 (remote-GUI): Manejador de evento EC en Interfaz Remota
../src/common/socket.cpp(292): assert "wxIsMainThread()" failed in Init(): sockets must be initialized from the main thread [in thread 7ff402d94700]


Call stack:
[00] wxOnAssert(char const*, int, char const*, char const*, char const*)
[01] 0x7ff42764be95
[02] wxSocketClient::DoConnect(wxSockAddress const&, wxSockAddress const*, bool)
[03] wxHTTP::GetInputStream(wxString const&) 
[04] wxSizer::Add(wxWindow*, int, int, int, wxObject*)
[05] wxSizer::Add(wxWindow*, int, int, int, wxObject*)
[06] wxThread::CallEntry()                   
[07] 0x7ff42733fe93
[08] 0x7ff42649d6fa
[09] clone                                   
Abortado (`core' generado)

---

