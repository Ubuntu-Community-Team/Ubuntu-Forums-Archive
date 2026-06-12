---
title: "Stability problems with BruteFIR on Ubuntu Server 12.10"
date: 2013-04-12
forum: General Help
---

### Post by a_tewinkel on 2013-04-12
[COLOR=#000000][FONT=verdana]I'm using a PC with BruteFIR as a crossover for my speakers. It has an AMD Athlon 64 LE-1640 2.6 GHz processor, a 2 GB compact flash card as a hard disk and uses a Terratec DMS 6Fire with optical S/PDIF input. Besides BruteFIR it also runs an Apache/MySQL server with Webfilter, a web interface to generate filters for BruteFIR.

I've recently reinstalled it with the latest Ubuntu server (12.10, the old OS was version 9.10) and I have disabled updates on the system to prevent them from messing things up. With the new installation I'm having issues with the stability of BruteFIR. Sometimes I hear some very unpleasant buzzing distortion which sounds like BruteFIR isn't getting enough priority (like the output is getting interrupted for some samples).

CPU load seems to be fine (about 35% idle, even when the buzzing kicks in) and most of the time it's running at only 1.8 GHz. At first I thought the CPU speed step kicked in too late (it was running at about 13% idle @ 1 GHz) so I changed the threshold for upscaling from 95 to 85%. I've also installed a low-latency kernel. At first this seemed to help, but the problem persists (although it occurs less often). The only thing I've noticed which might be strange is that already 95% of the 2 GB hard disk is in use, but I'm not sure if this is a lot for the newer version of Ubuntu.

I know it's a long shot, but does anyone have a guess at what might be the problem? I'm pretty much clueless at the moment...[IMG]http://cdn2.dastatic.com/forums/images/smilies/confused.gif[/IMG][/FONT][/COLOR]

---

### Post by a_tewinkel on 2013-04-14
I've also tried disabling the speed step, but this doesn't help either...

---

