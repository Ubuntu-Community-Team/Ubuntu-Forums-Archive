---
title: "USB hard drive unmounting randomly?"
date: 2007-12-28
forum: General Help
---

### Post by advanracing62 on 2007-12-28
Clean install from FF to GG- 
Issue was not existant on FF, is now on GG after about a month of use.
Noted that if i kill the bluetooth service the drive will unmount. 
today was the last straw- it didn't unmount, but is now saying in use... 
ideas?

---

### Post by tech9 on 2007-12-28
open terminal and type...

```
fdisk -l
```

then post output

when usb drive is mounted

---

### Post by advanracing62 on 2007-12-28
fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

no- USB drive listed here for some reason... though I'm playing MP3 from it now.

---

### Post by tech9 on 2007-12-28
> **advanracing62 said:**
> fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

no- USB drive listed here for some reason... though I'm playing MP3 from it now.

dev/sdb1 looks like your hard drive...

I think your problem stems from the system wanting to mount /sdb1 as your removable drive as well

---

