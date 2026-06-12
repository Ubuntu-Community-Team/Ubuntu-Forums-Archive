---
title: "Xorg is hogging over 1.5 GB RAM [Solved]"
date: 2007-09-15
forum: General Help
---

### Post by me1on on 2007-09-15
Recently Xorg has been hogging tons of RAM on my system. I have 2 GB of RAM, and Xorg is using 75% of it. Is this a problem with Xorg (memory leak) or with my system? Could it be beryl's fault? Has anybody else been having this problem? I've attached a screenshot of conky to show RAM/CPU usage.

---

### Post by MrHippocampus on 2007-09-15
ouch, that's probably a memory leak. My laptop has 2GB ram and I don't think its ever gone over 1GB actually being used by programs.

It could be beryl, so you could try running without it for a while and see what happens. A good idea would probably be to use your computer as normal and keep and eye on the ram usage to try and see what actions cause the ram usage to go up and not go back down.

---

### Post by me1on on 2007-09-16
> **MrHippocampus said:**
> ouch, that's probably a memory leak. My laptop has 2GB ram and I don't think its ever gone over 1GB actually being used by programs.

It could be beryl, so you could try running without it for a while and see what happens. A good idea would probably be to use your computer as normal and keep and eye on the ram usage to try and see what actions cause the ram usage to go up and not go back down.

Thanks. I tried waiting to see if what was causing this, but I still can't figure it out. When I turn my computer on, everything seems normal, but Xorg's RAM usage gradually climbs the longer the system is on. With Beryl turned on, the RAM usage hits about 90% in about an hour, whereas with KWin, RAM usage hits about 30% in an hour. I'm pretty sure it's a memory leak, but I can't find the bug anywhere. Maybe it has to do with my Nvidia card/driver? (Although it wasn't a problem about a week ago, and I haven't upgraded the drivers since then.) I could have upgraded to the latest kernel recently (not sure), but I don't know if that could've caused it.

---

### Post by me1on on 2007-09-16
Sorry for the double post, but for anybody who is experiencing the same problem I had, I seem to have solved my it. I'm using KDE, and in System Settings->Advanced->Session Manager->On Login, I had "Restore Previous Session" enabled (which is the Kubuntu default, I believe). I simply switched it to "Start with an Empty Session." I've had problems with the session restore feature before, so I'm not sure why I had it enabled. Hopefully the Kubuntu devs will change the default in the next release. :)

---

### Post by Maestro23 on 2007-09-16
Good deal man.  Don't forget to mark this SOLVED. (Edit your 1st post).

---

### Post by Cyclops_ on 2007-09-20
So I'm having this exact same problem with gnome.  I don't think that it's a beryl problem, because the same thing happens without beryl on...

The funny thing is that if I have beryl on, and everything starts slowing down, and I do a top, it tells me the problem is beryl and / or Xorg.  If beryl is not on, it points to Xorg.

The only way I have figured to stop the problem (and I have 3 Gig of RAM, mind you) is to restart.

Someone help!

(PS, on a similar note, and to help troubleshoot... how do I clear the RAM)

-----------------
WORK MACHINE SPECS:
Screaming CPU
3 Gig RAM
Really good nVidia video card
Feisty 7.04 (?)
Kernel 2.6.20-16-generic

HOME MACHINE SPECS: (happens at home too)
3000+ CPU
512MB nVidia video card
1 Gig RAM
Feisty 7.04 (Ubuntu CE)
not sure from here on the kernel

---

