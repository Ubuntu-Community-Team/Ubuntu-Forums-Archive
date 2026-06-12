---
title: "Ubuntu 20.04 - Xubuntu - Mouse input Stops working after a couple of minutes"
date: 2021-02-16
forum: General Help
---

### Post by john-morris-work on 2021-02-16
Hello,

 Not sure where to post this.
 
 
 I am getting ready to replace some old (486 grade) computer hardware with raspberry pi 4 (4GB). My software is an ongoing internal project over 15+ years and uses c++ and Qt 5. The touchscreens are Elographics 15" models with a USB interface. 

 On the RPi4, I installed Ubuntu Server 20.04, then installed build-essential, xubuntu-desktop, and qt5-default. I compiled my software, got everything configured, and did some light testing, with lots of reboots.  

 
 
   Everything went pretty good in testing, then I noticed if the RPi4 sat idle for more than a couple of minutes after a reboot, all touch/mouse input stops working. The only way I have found to get the mouse working again is to reboot. Again, it works great at first, then just stops after a short time period.
 
 
 Note, my software makes use of Dbus to inhibit all screensavers and power settings changes while it is running. Also, it does not make use of Qt’s touch interface, I’m just looking for ‘mouse clicks’ on the touchscreen.
 
 
 I use this same programming method (basically the same code) on a regular Xubuntu machine. By regular, I mean an Intel NUC with an i3, using the Xubuntu ISO to do the install. This machine never loses input, even when running for months at a time.
 
 
 On the RPi4, to start debugging, I use SSH to log in while the software is running and not responding to touches, I will issue a couple of commands:  “sudo libinput debug-events”  when I touch the screen, I see for example:
 
 
 [COLOR=#000000][FONT=monospace]event3   POINTER_MOTION_ABSOLUTE +4294967.295s  52.20/ 49.51 [/FONT][/COLOR][FONT=monospace]
event3   POINTER_BUTTON   +0.005s      BTN_LEFT (272) pressed, seat count: 1 
event3   POINTER_BUTTON   +0.111s      BTN_LEFT (272) released, seat count: 0 
event3   POINTER_MOTION_ABSOLUTE +1.122s        49.51/ 39.36 
event3   POINTER_BUTTON   +1.128s      BTN_LEFT (272) pressed, seat count: 1 
event3   POINTER_BUTTON   +1.208s      BTN_LEFT (272) released, seat count: 0

[/FONT][FONT=Calibri, sans-serif]then “sudo evtest”[/FONT]
 
 
 [COLOR=#000000][FONT=Monospace]Event: time 1613415861.162780, type 3 (EV_ABS), code 0 (ABS_X), value 2138 [/FONT][/COLOR][FONT=Monospace]
Event: time 1613415861.162780, type 3 (EV_ABS), code 1 (ABS_Y), value 2028 
Event: time 1613415861.162780, -------------- SYN_REPORT ------------ 
Event: time 1613415861.168781, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001 
Event: time 1613415861.168781, type 1 (EV_KEY), code 272 (BTN_LEFT), value 1 
Event: time 1613415861.168781, -------------- SYN_REPORT ------------ 
Event: time 1613415861.274778, type 4 (EV_MSC), code 4 (MSC_SCAN), value 90001 
Event: time 1613415861.274778, type 1 (EV_KEY), code 272 (BTN_LEFT), value 0 
Event: time 1613415861.274778, -------------- SYN_REPORT ------------ 
Event: time 1613415862.284926, type 3 (EV_ABS), code 0 (ABS_X), value 2028 
Event: time 1613415862.284926, type 3 (EV_ABS), code 1 (ABS_Y), value 16[/FONT][FONT=Calibri, sans-serif]12

So, it looks to me like the hardware is still working fine. [/FONT]Where do I start debugging next? I’m not sure of all the software in the input stack. X11? Lightdm?
 
 
 I guess I’m trying to find the differences between Xubuntu on my Intel i3 NUC, and Xubuntu on my Arm RPi4 that is breaking things.
 
 
 Any ideas?

---

### Post by john-morris-work on 2021-02-17
Follow up - this is Bug #1871767 - For now I'll work around the problem

---

