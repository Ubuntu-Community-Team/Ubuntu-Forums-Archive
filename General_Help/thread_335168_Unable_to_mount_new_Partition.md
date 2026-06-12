---
title: "Unable to mount new Partition"
date: 2007-01-09
forum: General Help
---

### Post by prepstyles on 2007-01-09
Hello.

I installed Ubuntu on a HD with the partitions already set up.
I mapped the partitions using the installer (the installer set up fstab).
I then choose to remove two of the partitions and create a single ext3 partiontion on the HD.
These partitions were not system critical ... meaning "/" and "/home" and "swap" were not mounted to them.
I then tried to edit fstab to reflect then changes and then ran "sudo mount -a" which resulted in:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
I've tried a number of things including reformatting the new partition with qtparted and run e2fsck on sdb3.
I'm reasonable convinced that the problem isn't with the partition but with the entry in fstab. 
I removed the entries in fstab for the partitions I removed and entered one for the partition I created.

This is fstab after the install (before I made changes):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2573b2ea-483c-443c-93e2-eb3f15a5d2be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=34C8E467C8E428B6 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=CC88A20E88A1F6DC /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=01C726D13F938000 /media/sda7     ntfs    rw,umask=0222 0 0
# /dev/sdb3
UUID=644C42484C421568 /media/sdb3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=0045-0B8D  /media/sdb4     vfat    defaults,rw,unmask=0000 0 0
# /dev/sdb2
UUID=407fb890-8b4c-4165-b023-0611f19d2ca1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

AND this is fstab as it is currently:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2573b2ea-483c-443c-93e2-eb3f15a5d2be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=34C8E467C8E428B6 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=CC88A20E88A1F6DC /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=01C726D13F938000 /media/sda7     ntfs    rw,umask=0222 0 0
# /dev/sdb3
/dev/sdb3 /media/sdb3               etc      defaults,users,umask=000 0       0
# /dev/sdb2
UUID=407fb890-8b4c-4165-b023-0611f19d2ca1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Please note that sda has windows ntfs partitions (ubuntu mounts them fine).

I'm wondering if I need to use the UUID of the new partition the way the installer did, and if so how? or perhaps it is int' necessary?

any advice is greatly appreciated!

Cheers!

---

### Post by yager on 2007-01-09
The last line shows a file format of etc?

The documentation for mount shows only the following supported formats.
>  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  coda, coherent, cramfs, devpts,
              efs, ext, ext2, ext3, hfs, hpfs,  iso9660,  jfs,  minix,  msdos,
              ncpfs,  nfs,  nfs4,  ntfs,  proc,  qnx4, ramfs, reiserfs, romfs,
              smbfs, sysv, tmpfs, udf, ufs, umsdos, usbfs, vfat,  xenix,  xfs,
              xiafs.   Note  that  coherent, sysv and xenix are equivalent and
              that xenix and coherent will be removed at  some  point  in  the
              future — use sysv instead. Since kernel version 2.1.21 the types
              ext and xiafs do not exist anymore. Earlier, usbfs was known  as
              usbdevfs.

Change etc to the correct type based on what you formatted the drive to using Gpartd.  This should correct the error after you type "mount -a" in a terminal window.

---

### Post by prepstyles on 2007-01-10
yager thanks for the prompt reply ....

> Change etc to the correct type based on what you formatted the drive to using Gpartd. This should correct the error after you type "mount -a" in a terminal window.

Turns out the etc was a copy past error on my part, the entry does say ext3 ...
and still doesn't work "sudo mount -a" stil generates the same error as above ...
here is the contents of fstab (for real this time .... *sigh*).


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2573b2ea-483c-443c-93e2-eb3f15a5d2be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=34C8E467C8E428B6 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=CC88A20E88A1F6DC /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=01C726D13F938000 /media/sda7     ntfs    rw,umask=0222 0 0
# /dev/sdb3
/dev/sdb3 /media/sdb3               ext3      defaults,users,umask=000 0       0
# /dev/sdb2
UUID=407fb890-8b4c-4165-b023-0611f19d2ca1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Again any feedback it appreciated ...

Cheers!

---

### Post by prepstyles on 2007-01-10
Just so no one waists time : ....
I reorganized my partition table and then reinstalled and mounted everything the way I wanted.
Problem solved!

Cheers!

---

