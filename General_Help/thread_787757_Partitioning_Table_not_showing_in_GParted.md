---
title: "Partitioning Table not showing in GParted"
date: 2008-05-09
forum: General Help
---

### Post by Dennetik on 2008-05-09
When I open GParted, it shows all of my harddisk as an 180GB piece of unallocated memory.
This same problem occurs when I try to install Ubuntu or Kubuntu from a LiveDVD/CD.

However, when I run fdisk, it shows my partitioning as following:

```
dennetik@sfeer:~$ sudo fdisk -l
Password:
omitting empty partition (5)

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8832    70943008+   7  HPFS/NTFS
/dev/hda2            8833        8865      265072+  83  Linux
/dev/hda3            8866       24321   124150320    5  Extended
/dev/hda4           10141       22916   102623188+   b  W95 FAT32
/dev/hda5            8866       10140    10241374+  83  Linux
/dev/hda6           22917       24191    10241406    b  W95 FAT32
/dev/hda7           24192       24321     1044193+  82  Linux swap / Solaris
```

The problem first occurred after I tried installing Kubuntu from a LiveCD.

What is this? How bad is this?
And, can I solve this?

---

### Post by Dennetik on 2008-05-09
Also, TestDisk reports a space conflict between the following two partitions.
/dev/hda3            8866       24321   124150320    5  Extended
/dev/hda4           10141       22916   102623188+   b  W95 FAT32

---

