---
title: "Got myself in a pickle with gparted - please help"
date: 2007-04-29
forum: General Help
---

### Post by dryder on 2007-04-29
Hi,
Edgy on /hdb
I was using going to use gparted to resize my partitions (/root was too small) but before making any changes thought I would copy (from within gparted) my /home partition on /hdb3 to a linux formatted partition on /hda2.

But in checking fstab afterwards terminal gives me:
david@server-ubuntu:~$ sudo mount /dev/hdb3
[mntent]: line 34 in /etc/fstab is bad
david@server-ubuntu:~$ 

fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a77cd4f7-f374-4724-95b6-226216ddf90c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=da00e25d-8a86-4a84-84d9-97c33bb122a8 /data           ext3    defaults        0       2
# /dev/hdb2
UUID=ed97c2dd-00b4-49ff-bfc6-7206ea8c1692 /home           ext3    defaults        0       2
# /dev/hdd1
UUID=FAE4F5C2E4F580E5 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=0088-2406  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4808736B087356C2 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=A628877928874771 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=8880A12E80A12422 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=DC6CB2456CB219EA /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=ae8b33e7-1f85-463f-b387-5c3af3ba352b /store          ext3    defaults        0       2
# /dev/hdb5
UUID=de3e64b8-8c5f-4145-8cc2-92de9b096fc0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda1
#/dev/hda1 /media/windows ntfs-3g defaults,locale=en_US.utf8,uid=1000 0 0
/dev/hda1 /media/windows ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0
# /dev/hda2
/dev/hda2 /media/hda2 vfat defaults, utf8,uid=1000 0 0

Can anybody please help me with the error on line 34 (presumably the last entry??)

Many thanks 
David

---

### Post by dcstar on 2007-04-30
> **dryder said:**
> Hi,
Edgy on /hdb
I was using going to use gparted to resize my partitions (/root was too small) but before making any changes thought I would copy (from within gparted) my /home partition on /hdb3 to a linux formatted partition on /hda2.
........
# /dev/hda2
/dev/hda2 /media/hda2 vfat** defaults, utf8**,uid=1000 0 0

Can anybody please help me with the error on line 34 (presumably the last entry??)

Many thanks 
David

Just guessing, but should the space be there between the highlighted items?

---

