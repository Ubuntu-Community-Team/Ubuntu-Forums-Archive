---
title: "Screen goes black after loading progress bar screen"
date: 2007-05-12
forum: General Help
---

### Post by FITorion on 2007-05-12
Turn on
Normal start up
Gets to the black screen with Ubuntu on it and a progress bar.  Once the progress bar finishes it goes to a black screen with only a blinking dash.

At this point it should go to the Ubuntu login screen.

Instead the screen becomes completely black.  No blinking dash or anything else.

I have successfully entered the "safe mode"/"debugging mode" which is just a terminal.


I'm fairly new at Linux so try to keep things as step by step as possible please.


running Ubuntu Edgy eft 64bit descktop

---

### Post by Dan Hammond on 2007-05-13
I seem to be having the sameproblem.
I installed ubuntu 7.04 yesterday and then it booted fine
After my screen shows the ubuntu status bar it also goes completely black but with mine there is a wait cursor.
After pressing ctrl+alt+f1 i got the terminal screen so i logged in as me and then rebooted and restarted in safe mode.
This however did not seem to work so i booted using my live cd and edited my sessions i dont know if this is exactly your problem; to start we are using different versions.
I think my problem was associated with a corrupt previous session because of a power cut.
Hope this helps, if it doesnt then i hope someone does but im quite a linux novice to be honest

---

### Post by FITorion on 2007-05-13
When it goes completely black there is no longer any HDD activity.

ctrl+alt+F1 does nothing same for +F2 +F3...

I have to hit reset to reboot.  on reboot I can enter recovery mode.  While there I did this:

startx

result = black screen/ completely frozen/ not even numlock on the keyboard would light up.

Update

I'm updating this from the machine in question.  I was able to boot into safe mode with the live cd I have.  ... I still have no Idea what's wrong... well I think it has something to do with X freezing my system but... I don't know why it's doing that or how to fix it.

---

### Post by phidia on 2007-05-13
Please provide your system specs including your gpu/graphics card. 
You may want to try the latest release.

---

### Post by FITorion on 2007-05-13
well I don't know exactly what you want...

vid card
NVidia GeForce 4 MX 4000 AGP 8x

mother board
Asus M2N32 WS Pro

um... yeah what else do you need to know?


It was working fine for the past 3 months or so.  I just turned it off... and when I turned it back on this problem occurred....

---

### Post by FITorion on 2007-05-13
Well I don't know what the problem was... But it's fixed.

A friend came over who is somewhat more wise in the ways of Linux... He found the Xorg.conf backup file and copied that over... and poof no more problem.



I can only guess that somehow the Xorg.conf file had gotten messed up. I have no Idea what did that.

---

