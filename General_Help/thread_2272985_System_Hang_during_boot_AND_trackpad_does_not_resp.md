---
title: "System Hang during boot AND trackpad does not respond to movement"
date: 2015-04-09
forum: General Help
---

### Post by skeeter-mcbee-y on 2015-04-09
Machine Information:
Lenovo G505s, AMD A10 5750M APU 2.5 Ghz w/ Radeon 8650G, 8 GB 1666 MHz DDR3 RAM
1 TB HDD, 600 GB Ubuntu, 300 GB Windows 8.1
Ubuntu 14.04 LTS, Gnome DE (both updated to latest version as of Apr 9, 2015), Kernels 3.17, 3.16.33, 3.16.34, 3.13

Problems:
Upon updating my system from Unity to Gnome this morning (Unity was being very slow and unreliable), I also applied an update which downloaded and installed Kernel 3.16.34 to my system. I let is slide because I was already running on 3.17 for the XBox One controller support. I am having a problem that I've seen on the forums before but have not been able to fix with their accepted solutions: My system hangs on start-up and leaves me with a blank gray screen. I can boot normally into the system with full functionality from the recovery menu, so I understand that this is a X server issue. I have already tried the generic video driver, FGLRX and FGLRX-Updates to no avail. Another issue I have had only happen in the last couple of boots is that my Elantech touchpad has stopped responding to movement. If I try moving my finger along it, it acts as though I am trying to click, but in the Mouse & Touchpad settings, I do not have a click response. The buttons attached to the trackpad work as expected, and I can use a regular mouse instead. I would be happy to comply to requests for more information within reason.

---

### Post by sandyd on 2015-04-10
Hi, can you attach /var/log/Xorg.0.log as an attachment please?

Thanks!

---

### Post by skeeter-mcbee-y on 2015-04-10
Unfortunately, I cannot. After seven hours of dealing with this machine, I decided to reinstall Ubuntu GNOME and restore my files from a scheduled backup that conveniently happened yesterday morning.

---

