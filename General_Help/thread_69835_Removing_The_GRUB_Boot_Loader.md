---
title: "Removing The GRUB Boot Loader"
date: 2005-09-28
forum: General Help
---

### Post by panthrax on 2005-09-28
I've done alot of reading on this and it is getting quite frustrating.

I have read and tried several methods already to try and remove the GRUB Boot Loader from my system and they all have failed or I have been unable to try them due to something blocking me from continuing. These methods are:

1. Use the fixmbr tool in a Windows XP installation CD. Well, my particular version of Windows XP is an OEM version so it doesn't contain all those handy tools I don't believe. Even if it did, when I try to boot from the disk, I get an error right after it detects the hardware and right before it starts the GUI for the disk. So that's out.

2. fdisk /mbr I have tried this also, and it seems to tell me "Wrong MSDOS version" when I had added FDISK and FORMAT programs to a standard Windows XP Professional Startup floppy.


So now what? I have Windows XP Professional on one hard drive, and Ubuntu on another, Windows being the master.

I installed GRUB to the MBR and I have already tried to format the hard drive that Ubuntu is on but when I do that, it locks up at the Boot Loader menu and won't allow me to continue to ANY operating system at that point.

This has become more trouble than it's worth. Please help me remove GRUB from the MBR so I can remove this problem-causing Ubuntu!!!

---

### Post by heimo on 2005-09-28
Have you tried overwriting it using something like (untested, unverified, potentially dangerous):
```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```
With of course, the correct device name for your boot disk.

---

### Post by Limulus on 2005-09-28
This thread might help you:
[http://www.neowin.net/forum/lofiversion/index.php/t367008.html](http://www.neowin.net/forum/lofiversion/index.php/t367008.html)

---

