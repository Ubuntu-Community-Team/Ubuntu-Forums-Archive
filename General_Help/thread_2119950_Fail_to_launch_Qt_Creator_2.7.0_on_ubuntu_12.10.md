---
title: "Fail to launch Qt Creator 2.7.0 on ubuntu 12.10"
date: 2013-02-25
forum: General Help
---

### Post by brucegu on 2013-02-25
Hi guys
I followed the guide [http://developer.ubuntu.com/get-started/gomobile/](http://developer.ubuntu.com/get-started/gomobile/) to setup the dev environment, and failed to lauch qt creator.
In Command Terminal I type the command line: qtcreator
I am given the error message: Segmentation fault (core dumped)
and if I type the command: sudo qtcreator
given the error message:
Qt at-spi: error getting the accessibility dbus address:  “Did not  receive a reply. Possible causes include: the remote application did not  send a reply, the message bus security policy blocked the reply, the  reply timeout expired, or the network connection was broken.” 
Accessibility DBus not found. Falling back to session bus.
      BTW: my ubuntu is upgrade from 12.04 to 12.10.
I am trouble in this error, I can not go on the tutorial.
Your reply is very appreciated.

---

### Post by brucegu on 2013-02-26
It still suffer me.

---

### Post by loell on 2013-02-26
have you tried re-installing the Qt Creator? also it seems that the preferred Qt Creator version for the Ubuntu touch repository is 2.6.1 not the newer 2.7.0

---

### Post by brucegu on 2013-02-26
I just follow that tutorial, it install qt creator 2.7.0 defaulty, I have no choice.
I have re-intalled qt creator many times.

---

### Post by brucegu on 2013-02-26
Sorry, It should be Qt Creator 2.6.82 based on Qt 5.0.1. I check that.

---

### Post by brucegu on 2013-03-01
No one knows this?

---

### Post by RubberJones on 2013-03-15
Hi [COLOR=#000000]brucegu,
[/COLOR]

I've still the same problem and didn't get a solution right now. Did you get it to work????
My system: Kubuntu 12.10, QtSDK5.0.1 
I get this message when I start QtCreator in a terminal: Segmentation fault (core dumped)

What I've tried:
I downloaded the qtcreator sources and compiled qtcreator by myself based on Qt5.0.1!
When I started the qtcreator(2.7.81) it throw out the same message.
Another try to compile qtcreator based on Qt4.8.3 seems to be working in the first moment. 
I get no error messages, but the IDE doesn't work correctly. The designer icon on the left side
isn't enabled and it is not possible to run a simple QML file with qmlscene.

---

### Post by mquinteiro on 2013-04-30
I got same problem and it was a incompatibility with fglx (I have nvidia and I don't need it) but with it qtcreator crash where launched. see dmesg or syslog to see if you have something like: 

 qtcreator[24329]: segfault at c ip 00007f30250c4170 sp 00007fff37ea43e8 error 4 in libxcb-glx.so.0.0.0[7f30250b9000+15000]

regards.

---

