---
title: "vfat partition icon on desktop automatically"
date: 2006-08-13
forum: General Help
---

### Post by playersgc on 2006-08-13
I'm running Dapper 6.06 on a Compaq laptop with Windows also installed on a separate partition.  Right now when I boot, I see an icon for the windows partition on the desktop.  I want to NOT see that one, and see instead an icon for my vFat partition that I use for storing data no matter which I boot with.  That is partition 4 (/dev/hda4) that I mount at /share.  Here's my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       /share          vfat    defaults,utf8,umask=000,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Even if I use System>Administration>Disks, to unmount the windows partition, it stays on the desktop.  "Disks" knows that /share is "enabled" but I don't seem to get an icon.

I'd also like to make sure that I won't write to the windows partition by accident.  Maybe I should not mount it at all?  Can I do that, too?

---

