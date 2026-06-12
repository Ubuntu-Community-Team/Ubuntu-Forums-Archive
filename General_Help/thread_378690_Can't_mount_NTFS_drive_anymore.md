---
title: "Can't mount NTFS drive anymore"
date: 2007-03-07
forum: General Help
---

### Post by ondre on 2007-03-07
I'm not quite sure when the problem started exactly but I can't mount one of my NTFS drives anymore with NTFS3G
> NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/hdb1': Invalid argument
The device '/dev/hdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


cfdisk -l gives me:
> Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   42  SFS


Is there a **SAFE** way to get it back?

---

### Post by taurus on 2007-03-07
Boot into Vista (do you have Vista on that harddrive, right?) and defrag or run a scan disk of /dev/sdb1.  Then, see if you can mount it again after you get back into Ubuntu.

---

### Post by ondre on 2007-03-07
Ran the disk scan in XP, took about 45 min.  Not sure if it found errors but it's still the same deal.

> Boot into Vista (do you have Vista on that harddrive, right?) and defrag or run a scan disk of /dev/sdb1. Then, see if you can mount it again after you get back into Ubuntu.

---

