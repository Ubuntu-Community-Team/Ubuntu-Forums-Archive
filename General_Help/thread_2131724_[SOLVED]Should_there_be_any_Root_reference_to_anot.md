---
title: "[SOLVED]Should there be any Root reference to another linux OS in /dev/mapper"
date: 2013-04-02
forum: General Help
---

### Post by Grafens on 2013-04-02
Is it normal to have root references to another linux OS within ubuntu /dev/mapper. The short story is I tried installing fedora18 onto some empty space (within an extended partition) it reinstalled grub and I could boot both ubuntu and fedora (didn't try windows) but grub gave me some errors when loading so I used boot-repair to correct this and now I can only boot into ubuntu and windows.
Ideally I'd like to have all three OS's bootable but I'm concerned especially with the reference to fedora-root within Ubuntu.

This is the output of fdisk
```
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x874fdd0d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920     1617919      768000    7  HPFS/NTFS/exFAT
/dev/sda3         1617920    75018239    36700160    7  HPFS/NTFS/exFAT
/dev/sda4        75018240   250068991    87525376    5  Extended
/dev/sda5       230539264   250068991     9764864   82  Linux swap / Solaris
/dev/sda6       127449088   230539263    51545088   83  Linux
/dev/sda7        75022336    76046335      512000   83  Linux
/dev/sda8        76048384    77072383      512000   83  Linux
/dev/sda9        77074432   127442943    25184256   8e  Linux LVM


Partition table entries are not in disk order


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d318e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001   83  Linux
Partition 1 does not start on physical sector boundary.


Disk /dev/mapper/fedora_ld-swap: 16.8 GB, 16844324864 bytes
255 heads, 63 sectors/track, 2047 cylinders, total 32899072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/fedora_ld-swap doesn't contain a valid partition table


Disk /dev/mapper/fedora_ld-root: 8942 MB, 8942256128 bytes
255 heads, 63 sectors/track, 1087 cylinders, total 17465344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/fedora_ld-root doesn't contain a valid partition table
```
Partition manager shows the layout differently with /dev/sda9 24.024GB as an unknown partition with a boot flag as LVM(the place where I was trying to install fedora).

Thanks

---

### Post by oldfred on 2013-04-04
Post link to BootInfo from Boot-Repair.

I posted this also in Boot-Repair mega-Thread.

RAID drivers are different than the lvm2 driver which is for LVM. Your  sda9 is LVM, so you need the driver to be able to mount and see inside  the sda9 partition. Many with Fedora on multi-boot systems just install  to a partition and not use the LVM.
Both some RAID and LVM  use a /mapper/...., so I think Boot-Repair can not be sure which you have.

---

### Post by Grafens on 2013-04-04
OK thanks it's sorted. I just mounted sda9 and did a grub-update

---

