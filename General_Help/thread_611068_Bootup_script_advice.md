---
title: "Bootup script advice"
date: 2007-11-12
forum: General Help
---

### Post by peedeeramone on 2007-11-12
Allright, this one is more out of curiosity than real need.  I want to create a script that will start a program, lets say my email client, evolution, when I log in to my username only.

I don't know a whole lot about bash scripting, but I'm trying to learn more, hence my experimentation

I would assume that this would be the proper script:

#!/bin/bash

evolution

simple enough, but what if I want it to automatically go to lets say the 4th workspace? I have no idea if that's possible or how to do it but yeah if someone could let me know that would be sweet.



also while I'm at it, is anyone familiar with MEPIS?

I am going to have to add a startup script on a MEPIS distribution in a few days and I was just wondering if since its a Debian based distro, would it work the same as Ubuntu? I've never actually used MEPIS before but from what I hear it's basically the same thing except KDE.

anyways just a couple of questions\

:guitar: <cuz he looks cool

---

### Post by dacap06 on 2007-11-12
The Linux Login process is highly customizable.  Among other things, it starts a bash login shell.  You can customize its behavior by creating a .bash_login script in your home directory (be sure to include the starting period in the file name).  In it, you can start your applications.  Anything put  in this file will start at login but not any other time.

If you want something to happen every time you start any bash shell, then modify the .bashrc script.

Hope this helps!

DaCAP

---

