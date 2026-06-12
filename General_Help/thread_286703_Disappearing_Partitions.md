---
title: "Disappearing Partitions"
date: 2006-10-28
forum: General Help
---

### Post by SirPecanGum on 2006-10-28
My partitions disappear after a period of time in Edgy. Generally my PC is on 24/7 so I know it wasn't happening in Dapper and if I go back to Dapper it still doesn't happen. 

Seems to take at least 5 hours before it happens in Edgy, any one have any idea as to why?

Incidentally, when I reboot my partitions reappear. Very strange!

Gparted correctly sees all partitions but warns that my NTFS partitions can't be read because I may not have the correct plugin - even though they work after boot.

---

### Post by SirPecanGum on 2006-10-28
Why does the fstab file look so different to the Dapper version? I don't have these UUID numbers in Dapper...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=2e4bdc16-648e-499b-96c0-cfe51142a981 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=AA9043639043355B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=5e5902ad-80bc-4f64-8c6f-f462699f629a /media/hda6     ext3    defaults        0       2
# /dev/hda8
UUID=8C61-1E54  /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdd1
UUID=02AC5FB3AC5FA049 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=92b0b8ea-55c3-4ff9-ba7f-7a07ce0c270b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by SirPecanGum on 2006-10-29
I modified my fstab file to look more like that of Dapper's, removing the UUID lines. So far all partitions are still available:

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdd1       /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6	/media/hda6	ext3	defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by phersotty on 2006-10-29
only thing I can think of is if you are using a user account that doesn't have permisions to mount the partitions.  For example root might be able to "see" and mount the partitions, but a normal user might not.  I haven't tried edgy yet...

---

### Post by SirPecanGum on 2006-10-29
Thanks for the idea. I did check my user account and with Nautilus as root but it didn't work. All still seems to be well since I modified the fstab file but I'm waiting to see what other problems my modifications will cause...

Actually, Fass explains it nicely here: [http://www.ubuntuforums.org/showthread.php?t=286758&highlight=edgy+fstab](http://www.ubuntuforums.org/showthread.php?t=286758&highlight=edgy+fstab)

---

### Post by SirPecanGum on 2006-11-03
I think modifying the menu.lst file as I have may have led to this problem. 

I boot Edgy from Grub installed with Dapper on another partition. I modified the menu.lst in Dapper to incorporate the new install of Edgy without using the UUIDs.

---

