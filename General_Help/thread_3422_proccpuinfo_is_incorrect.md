---
title: "/proc/cpuinfo is incorrect"
date: 2004-11-05
forum: General Help
---

### Post by diabolo on 2004-11-05
It says the clock is 400 when it should be 800. I have a 800mhz G3 iBook but here's what /proc/cpuinfo has when it's plugged into the AC adapter:

[dml@ubuntu:~]$ cat /proc/cpuinfo
processor       : 0
cpu             : 750FX
temperature     : 1-5 C (uncalibrated)
clock           : 400MHz
revision        : 2.2 (pvr 7000 0202)
bogomips        : 792.57
machine         : PowerBook4,3
motherboard     : PowerBook4,3 MacRISC2 MacRISC Power Macintosh
detected as     : 257 (iBook 2 rev. 2)
pmac flags      : 0000000b
L2 cache        : 512K unified
memory          : 640MB
pmac-generation : NewWorld

Also, when I use the CPU Frequency Monitor Gnome applet it says I'm at 400m Mhz (50%). 

:confused:

---

### Post by diebels on 2004-11-06
Play a video or something. Will make the applet show 100%

---

### Post by diabolo on 2004-11-06
Hey you're right about that. Thank you.

---

