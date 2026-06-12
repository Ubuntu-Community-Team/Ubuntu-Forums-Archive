---
title: "how do i keep drives from automatically mounting?"
date: 2008-02-10
forum: General Help
---

### Post by nkobel003 on 2008-02-10
I don't want my backup partitions to mount automatically.  How do I prevent them from mounting at startup?

---

### Post by FrozenFox on 2008-02-10
Mounting is dealt with in the file /etc/fstab (standing for file system table). I'm assuming you're using Gutsy as your info to the right suggests. This may work in hardy, but on mine I have no idea where the system put this information, as it isn't in fstab. Perhaps I'd have to add it myself. But since yours are auto-mounting, I doubt that's your case ;)

In the terminal/console/konsole:

1) Make a backup of fstab in case you mess it up on accident :) 
sudo cp /etc/fstab /etc/fstab.backup

2) Open the fstab file
sudo gedit /etc/fstab

3) Change the options line of the partition you want to stop from automounting to include "noauto". IE if you want hard drive 2 partition 6 to not auto-mount, youll find a line looking something vaguely like this (make sure you are changing the right one, you don't want to remove this stuff for the partition you are currently working on!):
 /dev/hdb6       /media/disk2   ext3  rw,user,exec 0 0

This is in the form:  
device/drivetype_whichdrive_drivepartition mountpoint filesystem options special-options

Change it to look like
/dev/hdb6   /media/disk2  ext3  rw,user,exec,noauto  0 0

Where drivetype is probably hd for a normal drive or sd for a SATA drive. Instead of the /dev/hdb6 or whatnot, you may have a UUID line. Be careful if that's the case that you are not editing your current system partition(s), once again.

4) Reboot, and see if it works as you wish. If something weird happens, restore your fstab via the inverse of part 1, ie sudo cp /etc/fstab.backup /etc/fstab.

If you need, in-depth info can be found here. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) but I don't think reading through that will be necessary for your problem.

---

### Post by 1875 on 2008-02-10
System - Preferences - Removable Drives And Media. May help.

---

