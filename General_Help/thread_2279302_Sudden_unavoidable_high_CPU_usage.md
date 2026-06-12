---
title: "Sudden unavoidable high CPU usage"
date: 2015-05-22
forum: General Help
---

### Post by Anna_Fedoruk on 2015-05-22
Hi,

I'm using 14.04 on HP ProBook 6360b. Sometimes it works perfectly, but from time to time (it happens everyday) something starts to use too much CPU. Usually it starts from Firefox: suddenly it starts to use more than 100% of CPU according to top. If I close Firefox, the next program I try to use (for example Chromium) starts to use too much CPU. Dash and everything appears to be very slow then. 

Sometimes it starts after hours of work, but sometimes it starts from the very booting: Dropbox starts to use more than 100% of CPU just after logging into the system. Sometimes reboot helps, but sometimes it doesn't.
I tried to google for solution but nothing works for me. I don't know what to do and how to diagnose what's wrong. 

Please help, I can't work normally, this issue takes at least three working hours from every my day :(

---

### Post by dino99 on 2015-05-22
both firefox & chromium use lot of power/ram; all depends about how many tabs are opened at once. Traffic can be reduced with appropriate settings (disabling the unneeded features/options, and blocking ads with adblock for example). Midori can be a lighter alternative.
Then the logs (xorg.0.log and dmesg) can help finding some usefull warning/error.

---

### Post by buzzingrobot on 2015-05-22
Try to identify the bad actor,  It's suspicious that Dropbox does sometimes peg the CPU immediately after it starts, if not always. I'd try disabling Dropbox's autostart (via "Startup Applications" in Unity) and all extensions and plugins in Firefox, rebooting, and seeing what happens,  If the CPU behaves, re-enable everything -- one thing at a time  -- including Dropbox, and see if that identifies the culprit. Log out and in after re-enabling Dropbox, and quit and restart Firefox when you re-enable something there. 

Keep top and/or System Monitor open while you're testing to see if any processes suddenly spike the CPU.

Might also be worth verifying it does not happen when a browser is never used.

---

### Post by Anna_Fedoruk on 2015-05-22
Thanks, I'll try this

---

### Post by Anna_Fedoruk on 2015-05-25
I've found that this issue is somehow connected with the source of power. For example everything works perfectly when my laptop gets power from battery, but when I plug in power cable everything starts to use too much of CPU as described in my first message. If I plug cable out everything works perfectly again.

But sometimes it works fine with plugged in cable.

What should I do for further investigation of the problem? Thanks!

---

### Post by Anna_Fedoruk on 2015-05-26
Looks like I've found the same problem here: [Slow down during power connection]("http://ubuntuforums.org/showthread.php?t=1921292")
So the solution is:

> To make this a permanent solution, create/edit /etc/modprobe.d/local.conf  to add the following line:
options drm_kms_helper poll=N

Works for me.

But it's rather strange that it's three years later and the bug is still here :shock:

---

