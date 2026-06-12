---
title: "Logitech LX7 Cordless Mouse not working on Gutsy"
date: 2007-11-18
forum: General Help
---

### Post by snideatlondon on 2007-11-18
Hi, I am trying to get my Logitech LX7 cordless mouse work on Ubuntu Gutsy.  While my standard PS/2 mouse was recognised during installation, LX7 wasn't.

lsusb shows a "Logitech, Inc. MX-1000 Cordless Mouse Receiver" in one of the ports but that's it. I have no response at all from my LX7 mouse, although it works perfectly when plugged into my Windows XP box. 

(full lsusb output is attached below)

sudo cat/dev/input/mice produces an output from the PS/2 mouse but is silent for LX7. 
similarly, sudo cat/dev/input/mouse1 only sees the PS/2 mouse. 
sudo cat/dev/input/mouse0 produces no output from either mouse.

dmesg reports something about "usb 2-3: usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -62" but I have no idea what this means. 

(dmesg output is attached)

could it be about my xorg.conf setup?

(copy of xorg.conf is also attached)

I would be very grateful for some help. I am new to Linux and this is driving me round the bend.

thanks very much

Ubuntu 7.10
Kernel Linux 2.6.22-14-generic
GNOME 2.20.1

---

### Post by snideatlondon on 2007-11-20
any ideas? 
even a RTFM clue would be very appreciated.
or should this request be posted at some other part of the forum?

---

