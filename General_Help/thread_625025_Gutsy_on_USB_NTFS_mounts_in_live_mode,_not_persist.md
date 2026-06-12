---
title: "Gutsy on USB: NTFS mounts in live mode, not persistent mode"
date: 2007-11-27
forum: General Help
---

### Post by emendelson on 2007-11-27
Gutsy on a 2GB USB stick, installed according to guide at:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Everything seems to work perfectly; all customizations "stick", except for this one problem:

When I try to mount an NTFS partition on the host machine in LIVE mode, it works perfectly.

BUT: when I try to mount the same NTFS partition on the host machine in persistent mode, I get this error message (in Nautilus):

Details:
mount: according to mtab, /dev/sda1 is already mounted on /media/C-WinXP 
FUSE mount point creating failed
Unmounting /dev/sda1 (C-WinXP)

/dev/sda1 actually isn't mounted on /media, and there's nothing at all in /media.

The output of fdisk -l is very strange also in persistent mode: when I first run it, it shows /dev/sda1 (etc.) for the hard disk and /dev/sdb1 and /dev/sdb2 for the USB stick. The next time I run it (in the same persistent session), /dev/sda has disappeared, though Nautilus still sees it.

I'm completely baffled by this. As I said at the start, NONE of these problems arise in live mode.

Thanks for any help.

---

