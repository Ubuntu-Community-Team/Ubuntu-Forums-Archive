---
title: "fstab help adding raid ex3 partition"
date: 2008-06-16
forum: General Help
---

### Post by barlrol on 2008-06-16
So just a little introduction.  I have 3 750 ntfs drives and then 2 more 750 drives that i set up as a hardware raid.  I installed raid and formatted the partition in ex3.  I can manually mount the partition by entering sudo mount /dev/mapper/sil_aiagcabifbah /media/movies.  But it wont let me edit anything because it says permission is denied.  I figure i need to add a line to mount this partition on startup.

first off the error:

tyler@amd:/media$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/dm-0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



tyler@amd:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xff3278db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1     1453517   732572536+   7  HPFS/NTFS

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x064cfd6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1     1453521   732574552+  42  SFS

Disk /dev/sde: 750.1 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xff3278dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1     1453521   732574552+  42  SFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04533558

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       29649   238155561   83  Linux
/dev/sdf2           29650       30401     6040440    5  Extended
/dev/sdf5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/dm-0: 1500.3 GB, 1500310536192 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table
tyler@amd:~$ 


HERES MY FSTAB



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c1a962cb-ae19-4c62-a216-805640aef5ab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=71adde8a-d3cd-40c1-b5c8-f125e8642b4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/dm-0       /media/movies   ext3  defualts  1  2

---

### Post by barlrol on 2008-06-16
well i figured out the problem...i spelled defaults wrong...also i needed to use the /dev/mapper instead of /dev 0 or whatever it was...It mounts now on boot, but I dont have permission to write files to it.  So that's my new problem.

---

### Post by drs305 on 2008-06-16
I can't figure out which partition it is you are trying to mount. To gain permission to edit a partition which you have already manually mounted use this command:
```
sudo chown -R **username:username** /path_to_mountpoint/mountpoint
```

---

### Post by barlrol on 2008-06-16
/dev/mapper/sil_aiagcabifbah /media/movies is where the partition im  talking about is being mounted to...if this helps.

---

