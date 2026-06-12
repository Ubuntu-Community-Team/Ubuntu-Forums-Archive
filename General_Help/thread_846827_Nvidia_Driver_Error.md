---
title: "Nvidia Driver Error"
date: 2008-07-01
forum: General Help
---

### Post by pwilczynski on 2008-07-01
OK, so to start off, I am a noob at Ubuntu. I used Windows my whole life, but I am looking at making the switch. So here's what happened.

I installed ubuntu, set up wireless internet with ndiswrapper and stuff, but I was stuck at 800x600 resolution. I tried a number of things to fix that, some of which were somewhat redundant. I used Xserver, and tried the default Nvidia driver. I have a 6600 GT. Finally, I edited the xorg.conf file, and suddenly my problem was fixed. I finally had 1024 x 768 as an option, and stuff was going great.

However, I was looking around, and the desktop graphics required me to install the nvidia driver. I said OK and restarted. However, now my screen is entirely messed up. Even during the very earliest BIOs, there are lines going down the screen. I can't read any of the boot options, and when I hit escape to try to go into the safe mode option, I can't find the right choice. If I just wait to boot up completely, the monitor shuts down as soon as Ubuntu is loaded. I am completely confused and I am fairly ready to reinstall; only I don't even think that that will help given the fact that stuff is messed up even in BIOs.

Any thoughts?

---

### Post by dcstar on 2008-07-02
> **pwilczynski said:**
> 
..........
However, I was looking around, and the desktop graphics required me to install the nvidia driver. I said OK and restarted. However, now my screen is entirely messed up. Even during the very earliest BIOs, there are lines going down the screen. I can't read any of the boot options, and when I hit escape to try to go into the safe mode option, I can't find the right choice. If I just wait to boot up completely, the monitor shuts down as soon as Ubuntu is loaded. I am completely confused and I am fairly ready to reinstall; only I don't even think that that will help given the fact that stuff is messed up even in BIOs.

Any thoughts?

Power off the monitor - as it looks like it is confused/broken.

See if you can obtain another monitor to test the system.

---

### Post by mempman on 2008-07-02
Can you go into your computer's onboard bios and see things clearly.  If not, your monitor is broken.

---

### Post by pwilczynski on 2008-07-02
No--BIOS is unclear and not completely functional. Would a new monitor lead to the same problem?

---

