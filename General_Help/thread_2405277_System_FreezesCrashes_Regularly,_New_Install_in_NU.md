---
title: "System Freezes/Crashes Regularly, New Install in NUC7i5"
date: 2018-11-03
forum: General Help
---

### Post by cmmichael on 2018-11-03
I have seen this problem with Ubuntu 18.04 posted quite often in the forums, without a definitive solution. I am an experienced user of Ubuntu and have been getting this instability on a new NUC box consistently since August.

Intel NUC7i5BNH Kit
Intel Core i5-7260U CPU @ 3.4GHz × 4 
Intel Iris Plus Graphics 640 (Kaby Lake GT3e)
7.8 GB memory
251.0 GB SSD
GNOME 3.28.2
1TB Hard Disk Drive

This is not a dual-boot setup. I first installed Linuxmint, after experiencing the freeze-up issues, usually with Chromium running, I switched to Ubuntu 18.04, and still have the same problem. The system also freezes occasionally while running videos in VLC. Here are some log files that appear in the "Important" section a lot:

xhci_hcd 0000:39:00.0: xHCI host controller not responding, assume dead

Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0

---

### Post by Autodave on 2018-11-03
The first thing that I would do with that box would be to get some air flowing around and through it.  Since your issue seems to be while surfing, I would definitely suspect overheating.  I am running a desktop here with 8 cores at 3.6 speed.  After a couple minutes on any browser, I hear the cooling fans ramping up.  I have a very large exhaust fan (added after purchase) and if you put your hand there it feels like a space heater.

Try putting a little fan next to it and see what happens.  I know that that is anoying, but it will tell you if that is the problem.  You could also leave the cover off of it.

---

### Post by cmmichael on 2018-11-05
Thanks for the input. There is no overheating happening with this problem. The first log file I listed above comes up every time with a freeze-up. I think my Googling has led me to at least narrow down the problem to the xHCI spec not working with linux. The wireless mouse I use (Logitech) works through a receiver plugged in to a USB 3.0 input.  The issue is addressed on this webpage: ( hamwaves.com - usb.autosuspend). It's a bit out of my skill level, but I might do another search for a recent fix. TIA for anyone who reads this and offers any help.

Update: switching off the wireless mouse and going with a usb plug-in has so far stopped the problem.

---

