---
title: "Xorg problem since recent Kernel Update"
date: 2018-02-08
forum: General Help
---

### Post by speartip on 2018-02-08
Ever since the latest batch of updates to "cure" the Meldown/Spectre virus issue, my system has taken a massive performance hit, & the culprit seems to be Xorg. In htop I have the following:
```
/usr/lib/xorg/Xorg -core :0  -seat seat0 -auth /var/run/lightdm/root/ :0  -nolisten  tcp vt7 -novtswitch
```
This can take upto 100% of 1 core & bring my FPS down from 30 to 6.
This happens on all instances of Ubuntu/Mint except KDE.
Any Ideas?

---

### Post by vasa1 on 2018-02-08
Could it be something related to the display manager with KDE using sddm not lightdm?

---

### Post by speartip on 2018-02-08
Hi Vasa1.
Those were my thoughts, as it does seem to be gnome/xfce centric. It also only appears to happen after a screen lock or resume from suspend. I have rolled back the kernel from 4.13xx to 4.4.0-112 to see if that resolves the issue, and will report back, for anyone else having the problem. This issue is not always apparent unless your system is put under heavy load. I only realised it by feeling my system was a bit sluggish and running glxgears.

---

### Post by speartip on 2018-02-08
This does indeed appear to be a kernel issue. On the 4.13 series kernel, within minutes xorg would be eating up my cpu. On the 4.4 series kernel I have now had 8 hours up-time with no issue.
I'll mark this thread as solved if all remains well for the next day or two.

---

### Post by bcschmerker on 2018-02-18
**Thanks for the heads up on a potential incompatibility.**  I'm looking at a non-negotiable situation for the Hot Rod gPC™, as the first-generation Advanced Micro Devices® Athlon 64® MPU is involved in a number of unable-to-start situations with Microsoft® Windows® 10.0.16299.192-up; mitigations for the Intel® Pentium Processors®/Core Processors™/Xeon Processors® rogue data cache load vulnerability (CVE-2017-5754) are implicated.  As of 17 February 2018 my rig runs an Athlon 64 3500+ on a Gigabyte® GA-MA78GM-S2HP, which I've already updated with Beta BIOS F6d in anticipation of an AMD Athlon II® or Phenom II® MPU (ideally the X4 910e, which runs at 2.6 GHz on 65*max* W).

---

