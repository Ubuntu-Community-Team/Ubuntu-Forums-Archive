---
title: "chmod on USB device"
date: 2007-03-18
forum: General Help
---

### Post by borobudur on 2007-03-18
Hi,
I'm trying to change the permission on a USB device. I put:
```
sudo chmod -R 755 /media/usbdisk
```But the permission stay the same *drwx------*

Is the /media-directory the wrong place to do that?

Regards
borobudur

---

### Post by yabbadabbadont on 2007-03-18
Most usb thumb drives (and others) use the fat32 filesystem.  It doesn't support linux permissions so what you see are set by the options used when the drive was mounted.  "man mount" for details and pay close attention to the "umask" option in the msdos and vfat sections of the man page.

---

### Post by borobudur on 2007-03-21
Hmm.. Do you have an idea how I could do this then? When I plug the usb the mounting is automatic.

---

### Post by yabbadabbadont on 2007-03-21
> **borobudur said:**
> Hmm.. Do you have an idea how I could do this then? When I plug the usb the mounting is automatic.

I *think* that is handled by HAL and pmount, so you might research them.  I never use the stuff myself.  I prefer having everything in /etc/fstab and only mounting media when I want it to be mounted.  It is just as easy with all the disk mounting applets and utilities that are available and you don't run into the kind of problems you are having.  :D

---

