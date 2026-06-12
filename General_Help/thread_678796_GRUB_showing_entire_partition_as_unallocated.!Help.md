---
title: "GRUB showing entire partition as unallocated.!Help."
date: 2008-01-26
forum: General Help
---

### Post by poisonblack on 2008-01-26
Hi.!

Gparted shows my entire partition as unallocated.Earlier I had used it successfully to create a separate /home partition.Then I started up Garted and it showed my entire partition as unallocated.!
Heres the content of sudo fdisk -l
```
Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37233722

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1714    13767673+   7  HPFS/NTFS
/dev/sda2            1715        2371     5277352+  83  Linux
/dev/sda3            2372        4864    20025022+   f  W95 Ext'd (LBA)
/dev/sda5            2372        2432      489919+  82  Linux swap / Solaris
/dev/sda6            2433        4211    14289817+   7  HPFS/NTFS
/dev/sda7            4212        4864     5245191   83  Linux

```
When I do Here's the content of sudo cfdisk /dev/sda, I get the following:
```
  FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap     Press any key to exit cfdisk

```

---

