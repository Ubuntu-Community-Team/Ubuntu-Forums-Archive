---
title: "Promise EX8350 SATA RAID on Feisty Fawn"
date: 2007-06-22
forum: General Help
---

### Post by madanasta on 2007-06-22
Has anybody been using a Promise EX8350 SATA RAID controller on Feisty? I got a problem with the following newly-made setup, related experience and ideas will be greatly appreciated:

SuperMicro PDSMA+ mobo
1x Western Digital WDC WD3200AAKS 320GB on on-board SATA
Promise EX8350 SATA RAID controller
2x Western Digital WDC WD3200AAKS 320GB on channels 1 and 5 of EX8350

The controller manages a single RAID 1 array consisting of the two WDCs.

After a few minor problems with GRUB immediately after install (wrong root information in menu.lst, solved it by hitting 'e' while on the grub boot menu, then manually changing hd(1,0) to hd(0,0), etc.), the system was otherwise running perfectly. The EX8350 and the array were detected by Feisty and I was able to create a partition and an ext3 filesystem on the array, mount it and use it. The problem first appeared when I did a large copy on the array (about 6000 files of various sizes, largest about 2GB, totaling about 70GB). Some time later, during a reboot, the EX8350 BIOS detected the array but reported it's state as 'Critical'. Further investigation using the controller's BIOS utility revealed that the array's RAID 1 configuration was missing one of the two drives, i.e. was reporting the array as consisting of drives on channels 1 and ?, rather than 1 and 5. The data was still accessible (as they should) and rebuilding the array took long (about 8 hours). After that, the array stayed at an 'Ok' state until a second large copy. Same behaviour then, only different drive lost off the configuration (drive on channel 1 this time).

As it is obvious that either I am doing something ridiculously wrong, or there's a problem with the controller and/or my setup, I was wondering if anybody has had any related experiences with a similar setup and the EX8350. Also, what troubles me is that the problem with the array configuration happens at a controller's BIOS level. Is there any chance that a OS driver can do that?? Doesn't it sound more like a hardware issue?

Thanks in advance for any ideas and suggestions.

mada

---

