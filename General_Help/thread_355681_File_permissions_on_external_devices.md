---
title: "File permissions on external devices"
date: 2007-02-07
forum: General Help
---

### Post by pureblood on 2007-02-07
When I plug in a usbstick or my camera in the computer, this is automatically mounted by the system and a link is displayed on the desktop. This is nice and practical. In the case the external device has been formatted with the vfat partition, the system automatically decides to assign to all files in the partition the read, write and executable permission only to the current user (that is umask=077).
This is very annoying since when copying the files on the computer the permissions are left the same and you end up with a bunch of files that the system believes erroneously that can be executed and that nobody else can read.

I would like to change this behaveour but I don't know which configuration files are responsible for this.
Also, I believe this shouldn't be the default behaveour since this problem was brought to my attention by an inexperienced linux user trying to copy the camera pictures on his websites with the result that the apache server couldn't read them because missing the right permissions.

Does anybody know which file I should edit to fix this (I want dmask=022 and fmask=133 that is more natural according to me)?

---

### Post by Topsiho on 2007-02-07
AFAIK the file you should consider is /etc/fstab
AFAIK the umask you need is complementary to what you need.

I do not know what you mean with "current user", permissions are assigned to owner, group and the rest of the world. If you want each to have permission to write and execute, the permissions should be rw-rw-rw- or in short 666. The complementary umask is 111.

Hope this helps.

Tosiho

---

### Post by pureblood on 2007-02-08
This doesn't help because it is not true that those informations are in /etc/fstab. You don't put informations on how to mount your camera in /etc/fstab since your camera or your usbstick are not part of your system. Somehow, the KDE system recognizes that a device has been plugged and through the hal daemon it mounts it on the fly. That way the user that is currently using the system is assigned as the owner of the device (with umask=077). But it is not clear to me which program is ultimately responsible for mounting the device.

---

