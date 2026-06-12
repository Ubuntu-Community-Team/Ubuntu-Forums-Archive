---
title: "hard drive acess"
date: 2007-02-10
forum: General Help
---

### Post by hendoc on 2007-02-10
I have Edgy on a 40 Gb Maxtor, which is the slave to 160 Gb WDC. I just reformatted Windows to oblivion and made the WDC fat 32. Edgy still does not see it in the file system. Am I going to have to reload Edgy to the larger HD, or am I just too green. Help!

---

### Post by pwrstick on 2007-02-10
Can you see the drive at all?

I.e. ```
sudo fdisk -l
```

Do you see it listed?

---

### Post by hendoc on 2007-02-10
hendoc@Exena:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
hendoc@Exena:~$

---

### Post by hendoc on 2007-02-10
sorry.Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         395     3172806    b  W95 FAT32
/dev/hda2             396       19457   153115515    b  W95 FAT32

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4791    38483676   83  Linux
/dev/hdb2            4792        4998     1662727+   5  Extended
/dev/hdb5            4792        4998     1662696   82  Linux swap / Solaris
hendoc@Exena:~$

---

