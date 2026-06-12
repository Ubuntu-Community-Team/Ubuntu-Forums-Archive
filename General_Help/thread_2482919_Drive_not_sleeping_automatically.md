---
title: "Drive not sleeping automatically"
date: 2023-01-14
forum: General Help
---

### Post by janne-m-boman on 2023-01-14
Hi
I have 2 spinning drives for bulk storage. The other one is sleeping automatically ok, but the other one not.
I have set standby time in drive settings, to no effect. If I send standby command manually from this menu, it works just fine. So drive seems to support standby.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291570&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291571&stc=1[/IMG]

Any ideas where to go next?
Thanks!

---

### Post by TheFu on 2023-01-14
At boot, perhaps setting the desired mode using 'hdparm' is needed?
```
NAME
       hdparm - get/set SATA/IDE device parameters

SYNOPSIS
       hdparm [options] [device ...]

DESCRIPTION
       hdparm  provides  a  command  line interface to various kernel interfaces
       supported by the Linux SATA/PATA/SAS "libata" subsystem and the older IDE
       driver  subsystem.   Many newer (2008 and later) USB drive enclosures now
       also support "SAT" (SCSI-ATA Command Translation) and therefore may  also
       work  with hdparm.  E.g. recent WD "Passport" models and recent NexStar-3
       enclosures.  Some options may work correctly only with  the  latest  ker&#8208;
       nels.
...
       -B     Get/set  Advanced  Power Management feature, if the drive supports
              it. A low value means aggressive power management and a high value
              means  better  performance.  Possible settings range from values 1
              through 127 (which permit spin-down), and values 128  through  254
              (which do not permit spin-down).  The highest degree of power man&#8208;
              agement is attained with a setting of 1, and the highest I/O  per&#8208;
              formance  with  a  setting of 254.  A value of 255 tells hdparm to
              disable Advanced Power Management altogether on the drive (not all
              drives support disabling it, but most do).
...

```

Just throwing out that idea.  I set other HDD tuning parameters in the system startup using 'hdparm' and 'blockdev' as well.

---

### Post by janne-m-boman on 2023-01-16
Thanks I'll give it a shot

---

### Post by TheFu on 2023-01-16
> **janne-m-boman said:**
> Thanks I'll give it a shot

Not all disks support spinning down. Some interfaces don't allow it as well.
I have some where I specifically don't want disks to spin down, but the interface refuses the commands.  I believe that spinning down and spinning up disks is what causes them to fail prematurely.  For 20 yrs, I've left computers on 24/7/366 and tried to have disks spinning always.  Seems to work.  I don't live in an earthquake area or near heavy construction that would cause the ground to vibrate, harming the spinning disks.

---

