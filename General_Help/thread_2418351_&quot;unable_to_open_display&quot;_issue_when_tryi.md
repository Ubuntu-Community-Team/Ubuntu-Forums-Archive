---
title: "&quot;unable to open display&quot; issue when trying to open Atom or even xhost"
date: 2019-05-05
forum: General Help
---

### Post by robhelvestine on 2019-05-05
Hello. I'm new to Ubuntu, so maybe this is an easy fix, but I can't find the solution online.
I downloaded Atom using apt, and now to open it, I type "atom" in the terminal and this the response

robhelvestine@DESKTOP-5738CRN:~$ atomrobhelvestine@DESKTOP-5738CRN:~$
(atom:28): Gtk-WARNING **: 18:35:04.429: cannot open display:

Looking around at proposed solutions, someone mentioned xhost. When typed, this is the response:

robhelvestine@DESKTOP-5738CRN:~$ xhost
xhost:  unable to open display ""

Can someone help me out? I'm on a Windows 10 machine and downloaded Ubuntu through the Windows App store. Thanks.

---

### Post by Holger_Gehrke on 2019-05-06
What you're using is not really Ubuntu, it's the Windows Subsystem for Linux (WSL) with some of the Ubuntu userland on top of it. WSL does not come with an X-Server, the basic component for doing graphics in a Linux environment. There are ways around that (basically: install an X-Server on Windows, point the environment variable DISPLAY at that), search for "WSL graphical applications" to find some tutorials.

Holger

---

### Post by dragonfly41 on 2019-05-06
Might be easier to install virtualbox in Windows and install Ubuntu image.
I have Windows 10 + WSL, plus Ubuntu in dual boot mode but I very rarely dip into Windows.
However Atom editor (atom.io) runs across Windows/Linux/Mac.
You can install Atom in Windows.

---

