---
title: "Help! Gparted doesn't recognize my partitions (more complex)!"
date: 2008-01-02
forum: General Help
---

### Post by djbon2112 on 2008-01-02
I've read the simmilar threads, but my issue seems more complex...

Gparted (including the liveCD version) just sees my entire 149 GB HDD as "Unallocated".
Qtparted gives me a fatal error saying "partitions cannot overlap".
TestDisk sees everything but I don't know how to use it and don't want to screw up my disks.

Anyone 
have any suggestions? This started when I switched my SATA mode from "AHCI" to "ATA" in BIOS for Windows to work properly, however now changing it back doesn't help.

---

### Post by sciencewhiz on 2008-01-03
what is the output of the following command:

```
sudo fdisk -l
```

---

### Post by djbon2112 on 2008-01-03
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1317    10490445    7  HPFS/NTFS
/dev/sda3            1318       19458   145710221+   f  W95 Ext'd (LBA)
/dev/sda4           19131       19458     2620416   dd  Unknown
/dev/sda5   *        1318        6040    37937434+  83  Linux
/dev/sda6            6041        6562     4192933+  82  Linux swap / Solaris
/dev/sda7            6563       18482    95747368+   7  HPFS/NTFS
/dev/sda8           18483       19130     5205028+   7  HPFS/NTFS

```
TestDisk sees this too, but neither of the others do.

---

### Post by sciencewhiz on 2008-01-03
I had a problem once where gparted didn't see any partitions when there was a file system error. Try checking all the partitions.

---

### Post by djbon2112 on 2008-01-03
Errr, not entirely sure how to do that in Linux!

---

