---
title: "Reformatted old windows partition to ext3, but can't mount."
date: 2007-07-03
forum: General Help
---

### Post by Bagleemo on 2007-07-03
Hi -

I happily came to the decision recently that I no longer need windows, so I formatted the partition ext3 using disk admin. However, I can't seem to make it accesible to put files on it. I'm using 6.10. I tried tweaking the fstab, but it still won't let me mount the newly formatted fresh windows-free partition.  Here is my fstab now. The partition in question is hda1.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    auto,user,exec,rw,async 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs auto,devmode=0666 0 0


Here is how it was after I formatted hda1 ext3 but before I started messing with fstab to try to make it work:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
none /proc/bus/usb usbfs auto,devmode=0666 0 0


Note: Hitting "Enable" on disk admin didn't work.... 

Any ideas kind ubuntu folks?

---

### Post by confused57 on 2007-07-03
This guide should work:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Bagleemo on 2007-07-03
Brilliant! Many many thanks!

---

