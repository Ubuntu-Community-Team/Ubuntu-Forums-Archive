---
title: "x11vnc fails from autoexec"
date: 2019-10-09
forum: General Help
---

### Post by Gourmand on 2019-10-09
Kubuntu 18.04 LTS. The x11vnc starts from KDE Autoexec folder in script:

#! /bin/sh
x11vnc -forever -noxfixes -noxrecord -noxdamage

After some activity in 5-10 minutes x11vnc fails. Then I start it with **all same options** from KDE console - it works without problem.

What can be wrong?

---

### Post by TheFu on 2019-10-09
I haven't a clue, but perhaps it needs to be launched detached from the parent process?
Also it is a *best practice* to fully specify the complete path to any programs called in a script, not trusting the PATH.  I dont use vnc, but would guess the program is in /usr/bin/

[https://www.tecmint.com/linux-process-management/](https://www.tecmint.com/linux-process-management/) is a reference for process control.  Just add an '&' to the end of the command line.

Just a guess.

---

### Post by HermanAB on 2019-10-09
You can try to put a "sleep 10;" in front of it, to allow the network dust to settle before it tries to start.

---

### Post by Gourmand on 2019-10-13
> **TheFu said:**
>  
fully specify the complete path to any programs called in a script, not trusting the PATH

But it starts nevertheless. Proper binary file - I checked. And from command line without path too. 

> **TheFu said:**
>   Just add an '&' to the end of the command line.

Just a guess.

Added. Did not help.

> **HermanAB said:**
> You can try to put a "sleep 10;" in front of it, to allow the network dust to settle before it tries to start.
Interesting idea... But as you can notice - I start it from KDE Autoexec folder. That means all dust must settle. But I will try your suggestion.

---

### Post by Gourmand on 2019-10-13
> **HermanAB said:**
> You can try to put a "sleep 10;" in front of it, to allow the network dust to settle before it tries to start.

Nope. It fails with sleep 10 before.

---

### Post by TheFu on 2019-10-13
Perhaps this is a dumb question, but are you trying to run the client VNC or the server VNC?  I vaguely remember the server  was called "vnc-server".

---

### Post by Gourmand on 2019-10-13
> **TheFu said:**
> Perhaps this is a dumb question, but are you trying to run the client VNC or the server VNC?  I vaguely remember the server  was called "vnc-server".

The problem is with VNC server called as [**x11vnc**]("https://github.com/LibVNC/x11vnc"). It's name is properly written in thread topic.

I did not tell first - in prev installation Kubuntu 14.04 it worked almost fine (some keyboard issues found). After OS upgrade it was upgraded to last stable version too.

---

