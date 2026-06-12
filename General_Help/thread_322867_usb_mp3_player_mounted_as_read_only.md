---
title: "usb mp3 player mounted as read only"
date: 2006-12-21
forum: General Help
---

### Post by kdavies on 2006-12-21
Hi 

Please can you help.

On Breezy, I have acl installed to be able to share a common directory.

I have just got a usb mp3 player, it is recognised by the system, but I cant write to the device.

I have looked through fstab, mtab and pmount settings but cant find where or how to change or check the current umask or vfat settings.

Even as root I can not touch a test file to the device.

The device currently mounts in /media/usbdisk

I have just tried a usb stick, works ok.
the device mount poins are different
The stick /media/USB DISK
The player /media/usbdisk

Any ideas?
Kevin

---

### Post by x64Jimbo on 2006-12-21
Is it maybe formatted as NTFS? That would explain the read only properties even while in root.

---

### Post by biffta on 2006-12-21
> **x64Jimbo said:**
> Is it maybe formatted as NTFS? That would explain the read only properties even while in root.

Agreed, plug in the player and type from the command line
df -T

That should tell you. If it is you may need to reformat it (fdisk maybe).

---

