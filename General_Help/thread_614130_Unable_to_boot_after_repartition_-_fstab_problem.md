---
title: "Unable to boot after repartition - fstab problem?"
date: 2007-11-15
forum: General Help
---

### Post by drwhitesnake on 2007-11-15
Hi

After repartitioning my hard drive I am now unable to boot normally although I am able to boot using recovery mode.  I think it is a problem with my fstab file but am not sure what I need to change.

fdisk gives this output:

```
 sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9de99de9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1836    14747638+   7  HPFS/NTFS
/dev/sda2            1837        5224    27214110    5  Extended
/dev/sda3           10634       19457    70878780    b  W95 FAT32
/dev/sda4            5225       10633    43447792+  83  Linux
/dev/sda5            1837        2080     1959898+  82  Linux swap / Solaris
/dev/sda6            2081        3658    12675253+  83  Linux
/dev/sda7            3659        5224    12578863+  83  Linux

Partition table entries are not in disk order

```

and gksudo gedit /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=2cf51f59-ad52-4aed-b372-73d5947ba8b2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0A745C17745C0839 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=938f96aa-b580-4572-aed4-2888abe18c72 /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=23d02c50-6240-4409-8c5e-24598907bb90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Am I on the right track and what next?

Thanks

---

### Post by taurus on 2007-11-15
> **drwhitesnake said:**
> Hi

After repartitioning my hard drive I am now unable to boot normally although I am able to boot using recovery mode.  I think it is a problem with my fstab file but am not sure what I need to change.

fdisk gives this output:

```
 sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9de99de9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1836    14747638+   7  HPFS/NTFS
/dev/sda2            1837        5224    27214110    5  Extended
/dev/sda3           10634       19457    70878780    b  W95 FAT32
/dev/sda4            5225       10633    43447792+  83  Linux
/dev/sda5            1837        2080     1959898+  82  Linux swap / Solaris
/dev/sda6            2081        3658    12675253+  83  Linux
/dev/sda7            3659        5224    12578863+  83  Linux

Partition table entries are not in disk order

```

and gksudo gedit /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=2cf51f59-ad52-4aed-b372-73d5947ba8b2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0A745C17745C0839 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=938f96aa-b580-4572-aed4-2888abe18c72 /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=23d02c50-6240-4409-8c5e-24598907bb90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Am I on the right track and what next?

Thanks

1.  Your swap is now /dev/sda5, not /dev/sda3 so you need to change that in /etc/fstab.

```
/dev/sda5   none   swap   sw   0   0
```

2.  You don't have /dev/sda2.  It is now an extended partition so you cannot mount an extended partition so you need to comment out that entry in /etc/fstab by placing a # in front of it.

3.  And perhaps I would also change an entry for / from "UUID=2cf51f59-ad52-4aed-b372-73d5947ba8b2" to /dev/sda4.

---

