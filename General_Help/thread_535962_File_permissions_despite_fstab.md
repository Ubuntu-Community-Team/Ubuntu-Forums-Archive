---
title: "File permissions despite fstab"
date: 2007-08-27
forum: General Help
---

### Post by Krudtugle on 2007-08-27
I have a mounted partition where I can't change file permissions and I don't understand why!

It's the folder /media/DATA/ which is actually a mounted partition.

laerke@ubuntu:/media$ ls -ltotal 32
drwxrwx--- 13 root plugdev 16384 1970-01-01 01:00 backup
lrwxrwxrwx  1 root root        6 2007-08-16 17:51 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2007-08-16 17:51 cdrom0
drwxr-xr-x  2 root root     4096 2007-08-16 17:51 cdrom1
dr-xr-x---  1 root plugdev  4096 2007-08-23 17:36 DATA
lrwxrwxrwx  1 root root        7 2007-08-16 17:51 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2007-08-16 17:51 floppy0
laerke@ubuntu:/media$ 

I intend to use that partition as the storage partition for pictures, music etc. but I can't write into it. So I've tried to change permissions with chmod (also with sudo), but that doesn't work.

So, then I read in the Ubuntu documentation pages that the permissions for mounted partitions are set in /etc/fstab, but that one looks fine I think:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=3be5f5ae-3ff9-4118-8413-455ce8cc4dfe /   ext3    defaults,errors=remount-ro 0   1
# /dev/sda2
UUID=085CA83B5CA82602 /media/DATA     ntfs    defaults,nls=utf8,umask=007,gid=46  0  1
# /dev/sdb3
UUID=4628-DCC9  /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=56E8585CE8583C85 /windows  ntfs  defaults,nls=utf8,umask=007,gid=46 0   1
# /dev/sdb1
UUID=9665b9b6-fbb2-4f67-8d7e-b2f85d17176f none    swap    sw       0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

What can I do? The /media/backup partition has the same rights in fstab, but in that folder I can write (add files) without problems...

---

### Post by kellemes on 2007-08-27
You need to have ntfs-3g installed for write access.
In fstab.. change ntfs into ntfs-3g

---

### Post by Krudtugle on 2007-08-27
OK, I'll try that. Thanks!

---

