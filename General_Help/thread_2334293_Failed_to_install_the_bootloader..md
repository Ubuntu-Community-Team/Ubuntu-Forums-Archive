---
title: "Failed to install the bootloader."
date: 2016-08-18
forum: General Help
---

### Post by mcdragon on 2016-08-18
Tried to create a USB installation disk using the Startup Disk Creator version 0.2.56.3ubuntu0.2 on Ubuntu 14.04. The version of Ubuntu I was trying to install was 16.04.1
The USB disk was erased several times through the Startup Disk Creator and the USB format was FAT32. At the end the error was:
> Failed to install the bootloader.
This happened repeatedly and on different computers with the same version of Ubuntu.

The forums suggest unetbootin however I was able to resolve the problem by reformatting the USB drive with the Disks (gnome-disk-utility) version 3.10.0 using zthe thorough (slow) method and using the same FAT32 format as before.
The Startup Disk Creator worked fine after that however it did ask to launch the package manager (which I cancelled).

---

