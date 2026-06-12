---
title: "Xorg error"
date: 2018-03-06
forum: General Help
---

### Post by dexmah on 2018-03-06
Good day. I am posting this from my phone as the Ubuntu laptop has no networking available. 
The system worked for about three months. Problems began with kernel 4.4.0-108. I deleted both kernel 108 and 109 upgraded to 112 and kept 104 as the back up. 
The problem is the system freezes upon the splash screen and a boot loop occurs.  If i use nomodeset the system freezes with the vg root recovery message . Using 104 kernel the system goes into low graphics mode. 
The only way the system will boot is if I do a system recovery. Then dpkg then boot only with kernel 104. Upon booting I have no network. Commands in terminal comes up with connection refused. In the error reporting there is a xorg error with screens not found. 
I also tried recovery from deja dup. I know the nvidia file needs updating. But with no networking this is not possible.
I attempted to use the live USB to either do a recovery or reinstall. I understand that all the system needs to do is update. The live USB which I used to install everything is 14.04 however the live USB is not booting. Freezing in the splash screen. 
What are my options. Any help will be greatly appreciated. I've been trying to fix this about a month now. 
Thanks.

---

### Post by TheFu on 2018-03-07
Sounds like a failing/failed GPU.

---

### Post by mc4man on 2018-03-07
Try booting up & removing the nvidia drivers in any fashion available to you
```
sudo apt-get purge nvidia*
```
If you can do from the desktop login fine or go to a tty (ctrl+alt+F3), login in & run command above. Or go to recovery > fsdk > root shell & do there.

---

### Post by dexmah on 2018-03-12
Did the above. ^
Got the message 
Note, selecting ' nvidia- prime' for glob 'nvidia*'
Note, selecting 'nvidia common' for glob 'nvidia*'
Note , selecting ' nvidia - libopencl1-dev' for glob 'nvidia*'
Note , selecting 'ubuntu- drivers common' instead of 'nvidia-common' 
Package, 'nvidia-prime' is not installed , so not removed
Package ' nvidia-libopencl1-dev ' is not installed, so not removed
0 upgraded 0 newly installed 0 to remove and 2 not installed

---

### Post by dexmah on 2018-03-15
Willing to reinstall everything and start over. However the live USB is also freezing. What options do I have ? 
Ubuntu is the only OS on the system. The OEM install from the live USB also freezes.

---

### Post by TheFu on 2018-03-15
> **TheFu said:**
> Sounds like a failing/failed GPU.

And this is making more sense to me.  Anyone else have an opinion?

Could be a failing PSU or failing motherboard (tiny cracks).  I've seen each of these 3 previously.  They don't happen often, but ...

---

### Post by dexmah on 2018-03-15
System starts every time I select dpkg in recovery. Everything fails though as there is not internet connection. System starts every time with limited usage. Such as no network. From the messages the system seems to revert to defaults.

---

### Post by TheFu on 2018-03-16
Sorry, when you said:

> The problem is the system freezes upon the splash screen and a boot loop occurs.
I assumed that the system was freezing and going into a boot loop.

I apologize for my misunderstanding.

---

### Post by dexmah on 2018-03-23
What will be my next step as I decided to do a fresh install. the live USB is also freezing. I used the same USB to do the initial install so I know it is working. However it is 14.04 and I upgraded to 16.04. I don't know if it will make a difference. Should I format my hard drive as the live USB is not booting ?

---

### Post by dexmah on 2018-03-29
I set parameters vga=791 on start up and system booted. however there was no networking and restrictions. i  understand the system needs to update to resolve issues but i am not sure how to get to that point. the live usb is still not booting.

---

