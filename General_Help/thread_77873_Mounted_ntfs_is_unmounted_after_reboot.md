---
title: "Mounted ntfs is unmounted after reboot"
date: 2005-10-17
forum: General Help
---

### Post by UbuntuUbuntu7 on 2005-10-17
Ntfs volume is unmounted after reboot, even though i have mounted it...

I would like to get this text:
*/dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222*

to  */etc/fstab*

but when i try to edit */etc/fstab*, i cant because its protected. I guess this should be done from a terminal. How?

---

### Post by seldenthuis on 2005-10-17
All filesystems are unmounted when you reboot, only those in /etc/fstab are remounted when you're computer boots.

You can open fstab by opening a terminal en typing 'sudo gedit /etc/fstab'. It's a system configuration file so you need to be administrator to edit it.

> /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
That won't work though. The line you need is:

/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0

---

### Post by UbuntuUbuntu7 on 2005-10-17
[QUOTE=seldenthuis]That won't work though. The line you need is:

/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0[/QUOTE]

:p Thank you that worked just fine. :cool:

but how do i delete this map: /media/windows ?
Because i made another one.

---

### Post by seldenthuis on 2005-10-17
sudo umount /media/windows
sudo rmdir /media/windows

The first command unmounts the partition and the second one removes the folder.

---

