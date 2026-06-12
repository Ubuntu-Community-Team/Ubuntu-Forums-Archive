---
title: "Login crashing"
date: 2008-06-15
forum: General Help
---

### Post by aperson on 2008-06-15
Hello,

whenever I try to login the X server crashes. The login manager works but after I entered user name & password an a second passed the X server crashes and a few moments later the login manager restarts again.

I can however login when I choose the failsafe gnome session. When logging in I got the following error message:
> Nautilus can't be used,
due to an unexpected error.

Nautilus can't be used right now, due to an 
unexpected error from Bonobo when attempting 
to locate the factory. Killing bonobo-activation-
server and restarting Nautilus may help fix the
problem

What also works is when I choose at the bootloader the older kernel version. Gnome then runs (in low graphics mode). I have installed the latest Nvidia drivers and not those from synaptic therefore I am forced into low graphics mode when loading a different kernel. If the exact version numbers of the kernels are relevant I can dig them out.

This problem only appeared after I installed a few updates yesterday, so probably it's the latest kernel in synaptic and the one before.

Thanks for your help.

---

### Post by aperson on 2008-06-15
I logged into the failsafe gnome session killed that bonobo app and tired to relogin. I still can't get into a normal session but when starting the failsafe version, there is no error message anymore and nautilus runs without any problems.

EDIT:
What is run in normal gnome that is not run in the failsafe version? I deactivated everything in System->Preferences->Sessions->Startup Programs and the problem still remains.

---

### Post by aperson on 2008-06-15
Has anybody got an idea what could be the problem?

---

### Post by unreality1490 on 2008-06-15
I'm having the same issue. Login manager seems to work without issue, but once i enter the pw something tries to load, my screen goes blank (no input msg) for a few seconds, and then I'm right back at the login screen.

Tried reinstalling ubuntu on same partition (from liveCD), then on another partition, then i used entire disk space. No luck any time.

Any ideas?

EDIT: The no input msg may be a separate driver issue.

---

### Post by aperson on 2008-06-15
I reinstalled the nvidia drivers and and overwrote xorg.conf with xorg.conf.original Now I'm no longer having login but logout problems! Gnome runs including the visual effects. However as soon as I go to System -> Quit Gnome frezes. I can restart gnome using ctrl + alt + backspace.

I have no idea what synaptic dig in that update yesterday but it really ****** up my gnome installation... 

Is there perhaps some way to do a reset of all gnome settings to their default? or some way to reinstall it?

---

### Post by aperson on 2008-06-15
Strange, after rebooting several times times gnome somehow seems to have fixed itself. :shock:

Oh well. I just hope it stays this way.

---

### Post by Wicked-Cricket on 2008-06-16
I'm getting the same message here on a fairly new installation of ubuntustudio. This appeared once right after installing the OS then haven't seen it again. Now that I have installed a new login theme its back. :sad:
Any suggestions?

---

