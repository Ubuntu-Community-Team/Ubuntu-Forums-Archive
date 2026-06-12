---
title: "Overclock Settings Ignored"
date: 2008-04-07
forum: General Help
---

### Post by Anthony M on 2008-04-07
I have my AMD 5200+ slightly overclocked from 2.7 to 2.9 Ghz, but Ubuntu will only run at the rated 2.7Ghz.

even when I disable the CPU freq scaling service it is still at the 2.7 speed. I believe the problem is the file:
```
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
```
is at 2.7Ghz and I do not have permissions to change it....

Any suggestions?

---

### Post by astoltz on 2008-04-07
I think (not positive about this) that the /sys directory is not stored on disk - instead it is a virtual filesystem created at boot time and contains information about the local hardware.  As such, It's probably not a good thing to change one of those files.  Also, I'd guess that since it's created during boot, it's getting the frequecy scaling directly from the hardware - or maybe the BIOS.

---

