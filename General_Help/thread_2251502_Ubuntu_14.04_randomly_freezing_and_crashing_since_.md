---
title: "Ubuntu 14.04 randomly freezing and crashing since installing a SSD"
date: 2014-11-04
forum: General Help
---

### Post by jordand2 on 2014-11-04
This might be a difficult one to solve. 

I bought a new SSD two weeks ago, a Samsung EVO 840 250 GB. I installed Ubuntu 14.04 on it, with Nvidia 331 OpenCL drivers for a GeForce 9800 graphics card. My motherboard is an ASUS P7P55D-E LX, a basic MB that has a mode where you can optionally tur USB 3.0 or SATA 6 but not both (I'm using SATA 6). The trade off is a halving of the memory transfer rate between the graphics card and MB (I'm mentioning this as it might be related). I have two other HDs, a 1TB and a 3TB, this is the same before (none of the HDs have write cache enabled). I have a 750 watt PSU, more than enough power. This is the first time I've used an SSD drive (and SATA 6), I'm very happy with the speed increase. However... 

... since installing the SSD Ubuntu occasionally locks up. The screen freezes nearly every day, the desktop is visible but frozen. And today after I turned on my computer and used it for 5, Ubuntu crashed when I clicked a window minimise button on Firefox (might not be related). I didn't have this problem before I installed the SDD. I tried REISUB (Magic SysRq key) when it locked up last night but that did work, I had to press the reset button on the case. The HD light was off, no activity.

I looked in the log, nothing stands out and anyway I would not know what too look for. SMART diagnostics are fine. On reboot there's no chkdsk, it just reboots as usual. Previously when Ubuntu locked up (usually due to a software problem) it automatically ran a chkdsk on reboot, but I have not seen it run since I installed the new SSD. Given the sudden freezing and now a crash, I suspect a hardware issue. I'm worried it might be a problem with the SSD.

Today Ubuntu crashed and gave the following cryptic message. It might help pinpoint the problem.

[ATTACH=CONFIG]257746[/ATTACH]

Any help would be much appreciated.

---

