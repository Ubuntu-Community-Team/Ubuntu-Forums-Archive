---
title: "USB Mouse Lag"
date: 2013-11-02
forum: General Help
---

### Post by jasonab1 on 2013-11-02
Good Day

I am running Ubuntu 12.04. About a month ago my PS2 mouse broke (my fist was involved). I plugged in a Wireless Logitech USB mouse I had and everything seemed fine until about 30 minutes into my session. I dont know how to  descibe it, the mouse is very slow to react, when it moves accross the screen it seems to skip and precise movement is difficult. Unplugging the receiver and plugging it in again did not help. I had to restart the computer each time. Everything works fine in windows. 

I tried the following:
[LIST]
[*]I installed updates
[*]changed some USB settings in the BIOS - did not work. Changed them back.
[*]update my Bios - did not work
[*]I then borrowed a cabled USB Microsoft optical mouse and the problem still occured.
[*]I uninstalled my graphics card drivers and installed the latest ones.
[/LIST]

I then decided to look for a USB to PS2 convertor so I could plug the USB mouse into the PS2 port, instead I found as PS2 mouse in the box. I plugged this in and left the USB mouse plugged in. Now the strange part. When the USB mouse lags, the PS2 mouse works perfectly. I am not sure what to try next other than buy a PS2 mouse, the problem is that most of the good ones are all USB. 
 
```
Linux jason-desktop 3.2.0-55-generic #85-Ubuntu SMP Wed Oct 2 12:29:27 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
```
jasonb@jason-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
```

---

### Post by CatKiller on 2013-11-03
It's not that strange; PS/2 & USB are completely different in how they function. My guess is that another USB device is causing interrupts on that IRQ. I don't know of a fool-proof way to fix that.

---

### Post by XBNCPRk on 2013-11-03
Not to sound dumb, but since it worked for a while then didnt... Whens the last time you changed your wireless mouses batteries? When they start to die, the signal from the mouse drops dramatically, and can easily cause jumping and non-responsiveness.

---

### Post by jasonab1 on 2013-11-06
:), the battery was the first thing I changed. It does it with a wired USB mouse as well.

---

