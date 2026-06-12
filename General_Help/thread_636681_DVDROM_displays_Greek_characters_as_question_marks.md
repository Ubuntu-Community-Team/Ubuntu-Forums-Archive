---
title: "DVDROM displays Greek characters as question marks"
date: 2007-12-10
forum: General Help
---

### Post by spirosta on 2007-12-10
I  Have the above problem and can't find a solution yet. When I insert a dvd with mp3 that have Greek names the names appear as question marks. I know that something is wrong with the encoding iso9660 but when i change it the dvdrom can't be mounted.  Here is my fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=07da1613-3c47-436a-a4b2-41e1bd75f428 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d0621e7d-9352-4a8b-ab2b-ab1ccbedbf0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,**iso9660** user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,**iso9660** user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
192.168.1.10:/mnt/Diafora /media/Diafora nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.10:/mnt/MP3 /media/MP3 nfs rsize=8192,wsize=8192,timeo=14,intr

With what should I change iso9660 so my files become again Greek?

---

