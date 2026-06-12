---
title: "ntfs partitions not mounted automatically"
date: 2006-12-23
forum: General Help
---

### Post by moonhk on 2006-12-23
Do you why ntfs partitions not mounted automatically ?

The hard disk is internal Harddisk( not USB harddisk).

What is ntfs-3g ? 

Is NTFS system mounted on ubuntu just allow user read only ? 


moonhk@HEX:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /nfts           ntfs    defaults        0           0


moonhk@HEX:/etc$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             19133332   3528572  14632832  20% /
varrun                  111776       136    111640   1% /var/run
varlock                 111776         4    111772   1% /var/lock
udev                    111776        96    111680   1% /dev
devshm                  111776         0    111776   0% /dev/shm
moonhk@HEX:/etc$

---

### Post by taurus on 2006-12-23
If you want your ntfs to mount automatically upon boot, you need to add an entry for it!  Here's a guide...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

And if you want to write to your ntfs, then you need to install ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by moonhk on 2006-12-24
Thank. I will try later.

Now, my machine can read/write vfat and read ntfs system.

root@HEX:/etc# cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdb1       /mnt/ntfs       ntfs    defaults        0           0
#/dev/hdb1        /mnt/ntfs       ntfs nls=utf8,umask=0222 0 0
/dev/hdb1         /mnt/ntfs       ntfs nls=utf8,umask=000 0 0
#/dev/sda1       /mnt/scsi       vfat    rw        0           0
/dev/sda1       /mnt/scsi       vfat iocharset=utf8,umask=000 0 0
root@HEX:/etc#

---

