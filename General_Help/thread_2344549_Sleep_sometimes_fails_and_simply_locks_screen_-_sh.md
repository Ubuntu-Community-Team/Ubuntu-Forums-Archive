---
title: "Sleep sometimes fails and simply locks screen - shutdown becomes impossible"
date: 2016-11-26
forum: General Help
---

### Post by andreluis-g-silva on 2016-11-26
Hello. Every once in a while, I put my laptop to sleep instead of shutting it down, for convenience. Everything works fine, except roughly 1/4 of the time, things don't work correctly.

Every time I put it to sleep, the screen turns black, and then alternates a couple of times between "black" and "pure black" (...I suppose that's the laptop's backlight turning on and off? *Shrug*). Normally, after this, the screen would shut down and the system would be asleep, but when the problem happens, the screen is still on, albeit black, and system lights are still blinking. Moving the mouse at this point reveals that the only thing the system did was lock the screen.

If I try repeating the sleep operation, the exact same happens. On top of that, from this point on, the system is running perfectly, except reboots or shutdowns will not work. By using the system's GUI to shutdown, I get the following message: ```
GDBus.Error:org.freedesktop.login1.OperationInProgress: There's already a shutdown or sleep operation in progress
```

If I try shutting down with **shutdown** or **reboot** in a terminal, I get a response saying how a shutdown has been scheduled for a minute or two from now, but that time comes and goes and absolutely nothing happens. This leaves me with no choice other than to forcefully power-down the machine.

Things I've tried:
[LIST]
[*]Running **shutdown -c** after a botched sleep order in hopes of clearing any stuck operation (even tried as superuser). 
[*]Keeping my system up-to-date. 
[*]Searching extensively for a solution or workaround...! 
[/LIST]

Relevant system specs:

[LIST]
[*]Lenovo Ideapad Y700
[LIST]
[*]8x Intel(R) Core(TM) i7-6700HQ CPU
[*]8GB RAM
[*]GeForce GTX 960M/PCle/SSE2
[/LIST]

[*]Ubuntu 16.04.1 LTS, 64-bit, Lubuntu flavor
[*]LXDE desktop environment
[*]Linux 4.4.0-47-generic (x86_64) kernel
[*]X11 Vendor is The X.Org Foundation
[/LIST]
 Thanks!

---

### Post by mörgæs on 2016-11-27
Hi, welcome to the fora.
For such new hardware I wouldn't install 16.04. I think it's worth a try to do a fresh install of 16.10.

---

### Post by andreluis-g-silva on 2016-11-27
Thanks for the welcome!

Honestly, everything else works  flawlessly, so I'm not sure if I want to go through the trouble of  backing up my documents and settings, do a fresh install on 16.10, and  then restore the backups, just for this one mildly-annoying occurrence.  But it's great to know that that is an option I have. If I can't find  any workaround and this begins to bother me, I'll be sure to give 16.10 a  try. Thanks!

---

### Post by mörgæs on 2016-11-28
A fresh install can be done without losing the old one. If you have the extra space one can add 16.10 in a dual boot.

---

### Post by andreluis-g-silva on 2016-11-28
Oh, I didn't know! I'll certainly have to try, then. Thanks!

---

