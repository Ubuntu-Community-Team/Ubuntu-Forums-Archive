---
title: "Wacom Woes"
date: 2006-08-30
forum: General Help
---

### Post by majesticturkey on 2006-08-30
I booted my computer this morning to find the CLI login window, which then flashed to the gray-background Xserver load screen (you know, the one with the X cursor that shows up sometimes), and back and forth a few times until X crashed. I looked at the output, and it complained of not being able to find /dev/wacom as it was loading. So I looked at the xorg.conf to see why it was looking for a wacom device that I never had in the first place. It seems Wacom is a type of stylus or something, which is weird. I don't have a tablet. This is a desktop, with a mouse, keyboard, and monitor. That's it. So I removed the Wacom devices from my xorg.conf and looked to see if it works now. Nope. "No screens found." So I reloaded the backup.

If I log in via CLI and startx, then it works just fine, no problems. I don't know what I could have done to prompt these Wacom lines to appear, the only device that I plugged in recently was a flash drive which I'd used many times before. Even crazier, it seems Xorg reverted back to using ati drivers instead of fglrx, which is what I installed and had been using.

Any ideas? I'm not at that computer now, so I can't get the full log of the x crash, but I will later. I doubt the hardware is going to matter too much, but I've got a 2.8GHz Pentium IV, 512MB RAM, 120GB HDD, Radeon 9800 Pro, Logitech USB mouse, PS/2 keyboard. Again, if I do a startx, it works just fine, but X crashes on startup with an error that it can't open /dev/wacom because it can't find the file (which makes sense considering I've never even seen wacom hardware).

:mrgreen:

---

### Post by cleentrax on 2006-08-30
Yeah, happens to me from time to time. When Ubuntu rebuilds xorg.conf, it adds a bunch of Wacom tablet/stylus crap. You can edit it out of your xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```

or you can try to replace xorg.conf with a previous backup.

---

### Post by majesticturkey on 2006-08-30
Well, I tried that. I took out the wacom stuff, and it gave me a "no screens found" error, right? It said that no matching device section was found for "ati" at BusID 1:0:1. In xorg.conf, my video card was set at BusID 1:0:0. So I changed it, and saw what happened. It gave the same error, only at 1:0:0. What does it want from me?

I tried reconfiguring xorg again, and nothing wants to work. It's very odd how this suddenly happened, but it seems pretty borked. But the oddest part is if I do a startx, it works just perfectly fine. ](*,)

---

### Post by majesticturkey on 2006-08-30
***SOLVED***

It was a neurological problem. My brain wasn't working.

When I removed the wacom sections from the xorg.conf, I forgot to remove it from the server settings list (the wacom devices were listed there, but their sections were commented out). When this happened, I ran a dpkg-reconfigure xserver-xorg. There was an issue with the video card drivers, but I just reinstalled xserver to fix it. That was the problem. When I did that, because I used to use xgl, the gdm.conf wanted to start up xgl, but I did not have xgl. So it errored, and all I had to do was fix the sections of gdm.conf and gdm.conf-custom. It works now.

---

