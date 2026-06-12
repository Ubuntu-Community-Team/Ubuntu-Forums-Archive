---
title: "fstab Help"
date: 2007-07-11
forum: General Help
---

### Post by narehart on 2007-07-11
I've got a SCSI and a SATA HD.  The SCSI has WinXP/ UBuntu dual boot.  The SATA is used for storage and has three partitions: FAT32, EXT3, and NTFS. Occasionally, when I reboot, fstab switches the device letter on the HD's turning dev/sda into dev/sdb and vice versa.  I then have to manually edit fstab if I want to access the partitions.

Here is some output.

sudo fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2295    18434556    7  HPFS/NTFS
/dev/sda2            2296        4753    19743885   83  Linux
/dev/sda3            4754        4866      907672+   5  Extended
/dev/sda5            4754        4866      907641   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   b  W95 FAT32
/dev/sdb2            4865       17632   102558960   83  Linux
/dev/sdb3           17633       30401   102566992+   7  HPFS/NTFS

```

And sudo gedit etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 
UUID=377bc599-5add-4145-b5ae-964401dd2479 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=99202971-d433-48f3-8ffc-cde34d226e19 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sdb1 /media/sda1 vfat user,auto,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda1 /media/sdb1 ntfs ro,auto,user,fmask=0111,dmask=0000 0 0 
#Added by diskmounter utility
/dev/sdb2 /media/sda2 ext3 rw,auto,user 0 0   
#Added by diskmounter utility
/dev/sdb3 /media/sda3 ntfs ro,auto,user,fmask=0111,dmask=0000 0 0 
```

As you can see,  I've corrected the fstab errors but this is only a temporary solution since the device letters will change again when I reboot.  I would really appreciate somebody's help on this one.

---

### Post by Nythain on 2007-07-11
just read another thread with this problem the other day, cant remember the link to it but you could probably search... i think ultimately the solution was using uuid's isntead of device names... you can get the uuid by typing blkid in the terminal... try that for a bit and see if it helps...

Edit: here's the other thread [http://ubuntuforums.org/showthread.php?t=492925&highlight=sda+change](http://ubuntuforums.org/showthread.php?t=492925&highlight=sda+change)

---

### Post by dreadlord_chris on 2007-07-11
you can fix this by mounting by UUID rather then by /dev point.
to find out what the UUIDs for each /dev point is:
```

ls -l /dev/disk/by-uuid

```
Now just replace the /dev/* points with UUID=... using the same format as sda2 & sda5 in your fstab

---

### Post by stchman on 2007-07-11
> **narehart said:**
> I've got a SCSI and a SATA HD.  The SCSI has WinXP/ UBuntu dual boot.  The SATA is used for storage and has three partitions: FAT32, EXT3, and NTFS. Occasionally, when I reboot, fstab switches the device letter on the HD's turning dev/sda into dev/sdb and vice versa.  I then have to manually edit fstab if I want to access the partitions.

Here is some output.

sudo fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2295    18434556    7  HPFS/NTFS
/dev/sda2            2296        4753    19743885   83  Linux
/dev/sda3            4754        4866      907672+   5  Extended
/dev/sda5            4754        4866      907641   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   b  W95 FAT32
/dev/sdb2            4865       17632   102558960   83  Linux
/dev/sdb3           17633       30401   102566992+   7  HPFS/NTFS

```

And sudo gedit etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 
UUID=377bc599-5add-4145-b5ae-964401dd2479 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=99202971-d433-48f3-8ffc-cde34d226e19 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sdb1 /media/sda1 vfat user,auto,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda1 /media/sdb1 ntfs ro,auto,user,fmask=0111,dmask=0000 0 0 
#Added by diskmounter utility
/dev/sdb2 /media/sda2 ext3 rw,auto,user 0 0   
#Added by diskmounter utility
/dev/sdb3 /media/sda3 ntfs ro,auto,user,fmask=0111,dmask=0000 0 0 
```

As you can see,  I've corrected the fstab errors but this is only a temporary solution since the device letters will change again when I reboot.  I would really appreciate somebody's help on this one.

Those /dev/sd(x) should not change.  They have never changed on me.

---

### Post by dreadlord_chris on 2007-07-11
> **stchman said:**
> Those /dev/sd(x) should not change.  They have never changed on me.

It happens though - it was one of the big factors in migrating to UUIDs

---

### Post by narehart on 2007-07-11
> **dreadlord_chris said:**
> you can fix this by mounting by UUID rather then by /dev point.
to find out what the UUIDs for each /dev point is:
```

ls -l /dev/disk/by-uuid

```
Now just replace the /dev/* points with UUID=... using the same format as sda2 & sda5 in your fstab

Worked beautifully. Thank you.

---

