---
title: "USB mount points"
date: 2007-09-09
forum: General Help
---

### Post by dad311 on 2007-09-09
I have two USB disks attached to my system.  Sometimes after a reboot the mount points will swap between the two disks.  Does anyone know how to stop this from happening?


thx

---

### Post by RingoP on 2007-10-06
I have this exact same problem and am looking for a solution. Really need a stable mountpoint to reduce hassle in running backups using rsync...

---

### Post by bodhi.zazen on 2007-10-06
mpt an entry in fstab to mout by label

See here :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by dabl on 2007-10-06
You need to "mount by UUID" to stop that -- USB devices get dynamically re-assigned, so you have to "nail" them down.

Basically, first```
 fdisk -l
``` while the USB drive(s) is connected and running. This will give you the CURRENT /dev/sd#

Now,```
 blkid
```

Now you have the information you need to write a mount line in /etc/fstab.  Here's what my NTFS-formatted thumb drive looks like:

# /dev/disk/by-id/usb-PNY_USB_2.0_FD_6E740900048A-0:0-part1  /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs-3g user,atime,rw,nodev,nosuid 0 0

Note the commented-out prior mount line, which had issues.

Note: Doing it this way pretty well kills the "hotplug" capability, as far as I can tell, so you'll need to plug in the USB drive before you boot *buntu.  If you hotplug it, you won't have permission to view or change the contents, at least that's what happens on my rig. :)

---

