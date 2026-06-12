---
title: "Edgy Constantly Freezing!"
date: 2006-11-03
forum: General Help
---

### Post by smartalecks on 2006-11-03
Recently updated from Dapper to Edgy. Update went well. Only problem is that Edgy Eft is CONSTANTLY freezing. Its very annoying. 

The entire system will freeze up (except for the mouse) seemingly randomly but every 5-45 minutes. When it freezes, I can still move my mouse but I cannot click anything or use the keyboard. It completely _FREEZES_, and I can only reboot to get it back to normal.

When it freezes I am doing something normal, such as browsing or using Writer or Bluefish.

Even while typing this I have had to reboot once ](*,)
Never had this problem before.

Specs:
AMD Athlon 2800+
KT600 Dragon Ultra
1024mb ram
GeForce 5500fx (256mb)

FYI I don't think that the problem is with the hardware, but they are there if anyone asks.

---

### Post by jmeadows111 on 2006-11-03
It may be that your Xorg is having issues; I was seeing the same kid of thing on my PC before I did a clean Edgy install (previously I was using Dapper, and trying out the Beryl stuff).

The system seemed unresponsive, but I was able to ssh in from another computer, and saw Xorg taking up 99% CPU. I killed the xorg process and got a console back, and restarted X.

I don't know what precisely caused the issue (and I haven't seen it since I moved to Edgy) but it might be worth trying this test if you can to see if it is the same issue. Hope this is some help.

---

### Post by volfro on 2006-11-09
I'm actually having a similar problem.

I upgraded to edgy (clean format and install, though my home partition remains unchanged) and since experience seemingly random freezes. Unlike OP, though, my mouse even freezes. The system completely halts. Once, it rebooted itself, but every other time I've had to do a hard reboot, which is bad. 

It doesn't happen as often as the OP--maybe once every couple of days--but it happens, and it shouldn't. I have a similar system to the OP as well.

Anybody else having random freezing issues, or should I check my hdd out?

---

