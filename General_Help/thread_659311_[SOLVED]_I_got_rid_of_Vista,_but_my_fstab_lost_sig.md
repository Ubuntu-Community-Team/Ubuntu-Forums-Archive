---
title: "[SOLVED] I got rid of Vista, but my fstab lost sight of Xp!"
date: 2008-01-05
forum: General Help
---

### Post by lvaillan on 2008-01-05
I would like fstab to mount my ntfs partition with r/w/execute rights, but I'm not sure how to proceed :(. From what I can understand from googling around, the output of ls /dev/disk/by-uuid -alh might be usefull in getting help, along with fdisk -l and  my fstab.

drwxr-xr-x 2 root root 180 2008-01-05 15:44 .
drwxr-xr-x 6 root root 120 2008-01-05 10:44 ..
lrwxrwxrwx 1 root root  10 2008-01-05 10:44 07D5-0709 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-01-05 10:44 4AA02C3CA02C30BD -> ../../sdb2
lrwxrwxrwx 1 root root  10 2008-01-05 15:44 572ef688-e269-491f-8047-6043312a2cf3 -> ../../sdb6
lrwxrwxrwx 1 root root  10 2008-01-05 15:44 d4c920a6-78df-453f-93e3-e6f30a1bc196 -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-01-05 10:44 d971fc16-c8d1-43e8-9bd2-9d827ce4cea5 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-05 10:44 ebf90bd5-bbe1-4700-971c-91fea74b1840 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-01-05 15:44 f67af37d-13ce-4bbb-8678-f263a3f2a4bd -> ../../sdb7
luc@luc-desktop:~$ 

Here is my fdisk -l output:

Disque /dev/sda: 320.0 Go, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca8f7d7f

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disque /dev/sdb: 250.0 Go, 250000000000 octets
255 heads, 63 sectors/track, 30394 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeede9d79

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           8       25505   204812685    7  HPFS/NTFS
/dev/sdb3           30035       30393     2883667+  db  CP/M / CTOS / ...
/dev/sdb4           26117       30034    31471335    f  W95 Etendu (LBA)
/dev/sdb5           26117       26247     1052226   82  Linux swap / Solaris
/dev/sdb6   *       26248       27762    12169206   83  Linux
/dev/sdb7           27763       30034    18249808+  83  Linux


And now, my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d971fc16-c8d1-43e8-9bd2-9d827ce4cea5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ebf90bd5-bbe1-4700-971c-91fea74b1840 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


How can I mount all my partitions (linux and windows) with complete  rights? Is there a GUI for fstab?

lukobenjito

---

### Post by lvaillan on 2008-01-05
Ok, I have just changed my fstab to this and the Windows part of my question is solved: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d971fc16-c8d1-43e8-9bd2-9d827ce4cea5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=4AA02C3CA02C30BD /media/sdb2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=ebf90bd5-bbe1-4700-971c-91fea74b1840 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

But I want to proceed with extra care mounting my linux partitions. I've made some change on my girlfriend laptop (reformated a ntfs partition to ext3) and I'm trying to learn a bit about fstab before I edit anything.

---

