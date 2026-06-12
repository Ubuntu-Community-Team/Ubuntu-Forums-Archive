---
title: "Can't sync BIOS and ubuntu hardware clock (to local time)"
date: 2016-05-02
forum: General Help
---

### Post by f(fanta) on 2016-05-02
I am trying to have the BIOS clock of my PC, ubuntu hardware clock (as reported by **hwclock**) and ubuntu time (as reported by **date**) all on local time. However, ubuntu keeps setting the BIOS clock to UTC.

Here what I have done:

[LIST]
[*]made sure ubuntu is showing the correct local time, including time-zone and DST (with **date** command, or in the upper right corner of the desktop) 
[*]added** UTC=no**  to **/etc/default/rcS** 
[*]issued** sudo hwclock --systohc --localtime** 
[/LIST]
 now **sudo hwclock --show** reports that the hardware clock is on local time, as desired, but when I reboot and go into the PC BIOS, the clock is still on UTC!

Any clue how I can have the BIOS clock and ubuntu hardware clock report the same (local) time?

Running ubuntu server 16.04 64-bit with Unity desktop.

---

### Post by f(fanta) on 2016-05-02
I manually changed the clock in BIOS, so it matches local time, and at the next boot ubuntu was still showing local time with both  **hwclock**  and **date**. So I got all the clocks on local time, as desired. I leave the post here in case somebody has the same issue. BTW, this also fixed a mis- alignment between the clock of Windows 10 and that of ubuntu.

---

