---
title: "USB stick problem-can't read superblock"
date: 2008-07-03
forum: General Help
---

### Post by woland82 on 2008-07-03
here is the message I get when I insert my USB stick:
> Cannot mount volume
unable to mount the volume
mount:/dev/sdb: can't read superblock

I tried this:
> sudo mkdir /media/sdb
sudo mount /dev/sdb /media/sdb


And I got this message after I entered the last command:
> mount: /dev/sdb: can't read superblock

Here are results from fdisk -l
> naida@naida-laptop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ccd472d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris

Disk /dev/sdb: 1014 MB, 1014497280 bytes
32 heads, 61 sectors/track, 1015 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1478321     1478349       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


And results of cat /etc/fstab:
> naida@naida-laptop:~$ sudo cat /etc/fstab
[sudo] password for naida: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=067e88c6-8633-41ca-9332-32b11c73ce83 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1525df5a-b06a-447e-95e1-5a9a1bd684c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
naida@naida-laptop:~$ 



Please, help! Thank you!

---

### Post by Argard on 2009-04-26
Same problem here with a 8GB stick.

```
Disk /dev/sdb: **8472** MB, 8472494080 bytes
64 heads, 32 sectors/track, 8080 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x20736f63


This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      936098     1756816   840415161   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      945773     1776699   850868148+  ff  BBT
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      863407     1726748   884061367   6c  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1409025     1409051       27107    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by altxerror on 2011-01-05
i had the same problem, but with an sd card.

heres how i fixed it.

load terminal then type in

```
df
```

this will display your drives. find the non working usb drive and memorize it's dev name.

once ready, type in

```
sudo apt-get install gparted && sudo gparted
```

this will install and run gparted

once there, find your drive.

click on the main partition, then right click then choose delete/remove

then right click again and choose new...

manually set the information from here (for 8 gbit, take 12 mb off and splice into 2 unallocated parts as backup)

type in what you want the device name to be, then choose the file system (i prefer fat32, cause it's multi compatible)

then click ok.

then click on the check mark to commit changes. and your done. it should now work.

unfortunantly, it'll erase all data on the disk. so be sure this is what you want to do before trying!

---

