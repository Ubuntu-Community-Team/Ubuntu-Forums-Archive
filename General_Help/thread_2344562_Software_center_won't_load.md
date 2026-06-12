---
title: "Software center won't load"
date: 2016-11-26
forum: General Help
---

### Post by l6griffin on 2016-11-26
hp laptop
Device: HP 2000 -2D64
Memory: 7.4 GiB
Processor: AMD E1-1500 APU with Radeon(tm) HD Graphics × 2 
Graphics: Gallium 0.4 on AMD PALM (DRM 2.43.0, LLVM 3.8.0)
OS Type: 64-bit Ubuntu 16.04 LTS
 
when I try and bring the software center up the screen loads and then all I get it is a circle indicating it is working. I uninstalled then installed software center and no help same results.

I have been getting notices of system crashes that seem to be attributed to gnome. The crashes have been reported.

Larry

---

### Post by ajgreeny on 2016-11-26
This is a known and reported bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1573206)

Try synaptic instead or use the terminal and ```
sudo apt install packagename
```

---

