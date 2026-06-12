---
title: "kubuntu hangs when system is idle"
date: 2007-04-09
forum: General Help
---

### Post by bartosz.wadolowski on 2007-04-09
hi

i'm using up-to-date kubuntu 7.04. when my system is idle for about 30 minutes system hangs. system is idle means that i don't use keyboard and mouse. hangs means that i can't do anything but keep power button pressed for 4 seconds until my laptop shoutdown. but applications doesn't hang, for example, amarok is playing music i can even see analyzer visualization. keyboard doesn't respond at all, i've tried ctrl+alt+del, ctrl+alt+backspace(sometimes works but very rare, but closing Xorg only begins never actually been closed), alt+ctrl+f*. in most cases i'm able to move my mouse cursor, and when i move it under, for example, menu then this menu item is highlighted, but when i click on anything, nothing happens. 

i have all power saving options turned off, all means in screen saver module, in kubuntu power manager and in monitor & display module. i couldn't find any other options related to power saving. i'm using linux from day one on this laptop. my previous installation was edgy upgraded to feisty and i everything was ok. this is quite fresh feisty installation and it happens since i've installed it. no sign of anything suspicious  in any /var/log nor in .xsession-errors file.

ok now finally is time for my questions. 
do anyone have any clue what can trigger this? i know that it is because system idle, but what process is monitoring my input devices? 
and maybe some one had something similar even caused by something else but system was frozen in the same way?
i have 3 suspects: acpi kernel module, hal deamon and Xorg. but i couldn't find any clue in Xorg.log nor in .xsession-errors. and do anyone know where i can find hald logs?

i don't require answer how to fix this, but any clue what can cause this will be very helpful.

bartek

---

### Post by esdaniel on 2007-04-30
Sorry not to have any smart ideas to share but... as this post is over 3 weeks old did you ascertain what the problem was?

I've had the same issue as well although the screensaver was normally active then the screen display corrupts i.e. meshed multicolor pixels of no determinate image - in earlier FF builds the issue was not there so the only yardstick I have is that is was around 2.6.20.13-.15 of the kernel version released when I noticed this occurring and like you I'd appreciate any tips on how to bug-hunt this one.

---

### Post by pyrforos on 2007-05-04
same thing here....any solutions guys?

---

### Post by esdaniel on 2007-05-04
The recent updates (made available yesterday or day before) seem to have fixed this problem on my setup.

---

### Post by pyrforos on 2007-05-14
nothing for me.... its really getting frustrating!!:(

---

### Post by rickdog on 2008-02-04
Hey there, just checking to see if anyone has found a solution to this problem. I'm having the same issue on my laptop with Gutsy.

---

