---
title: "transfer music directories from Ubuntu desktop to Android Samsung Galaxy S7"
date: 2016-06-20
forum: General Help
---

### Post by Old Jimma on 2016-06-20
HI Community:

I bought an Android Samsung Galaxy S7 ... and put a 64Gb microSDXC card to augment its capacity. It is a new model Android, so it probably has the most recent Android operating system.... I don't know much about that.

I want to transfer music directories on my Ubuntu desktop that have music to the Android.

When I plug the Android into my Ubuntu desktop I don't see anything... no directories or anything.

Can somebody tell me how to transfer those music directories from my Ubuntu desktop to my Android's microSDXC card so that I can see them on the Android and play them?

Many thanks,
Old Jimma

---

### Post by Bucky Ball on 2016-06-20
You need exfat-utils and exfat-fuse installed to access SDXC cards. They are both in the repositories.

---

### Post by TheFu on 2016-06-20
It is possible to format 64G and larger SD cards with FAT32 and this will work fine back in Windows and with other systems. It is just the "format" step which MSFT doesn't support natively over 32G anymore.  3rd party tools on Window will allow larger sizes. The 32G limit for storage was added around 2000-2002 (MSFT wanted a new patent, hence exfat was created). Prior to that, FAT32 would format much larger disks. 

Found this old reference [http://www.tomshardware.com/forum/173432-48-hard-drive-size](http://www.tomshardware.com/forum/173432-48-hard-drive-size) which says FAT32 should support 2TB disks, though it gets slower as the size increases. 

Whether using it on Linux without a license is legal is dependent on the laws in your location. I don't believe it to be legal in my jurisdiction, unless Canonical paid the fees for us. [http://arstechnica.com/information-technology/2009/12/microsoft-licenses-out-exfat-file-system/](http://arstechnica.com/information-technology/2009/12/microsoft-licenses-out-exfat-file-system/) 

Linux FAT32 tools will format it fine. I've done this for a 64G SDHC device, but will admit to seeing more file corruption with embedded devices having issues (video recorders). It will work for weeks without any issues, then I'll have to run a disk clean up on Windows to find some lost files and clean up the allocation table.

With my Nexus4, I had to manually do some things to make it work with Ubuntu 14.04. [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) explains. Don't know if this is necessary for an S7 or not. On 16.04, it *just worked.* which was nice.  I don't see any useful files under /dev/udev/, so I'd guess that systemd changed what would be necessary on 16.04 to manually configure newer devices, if needed.

Anyway, see that Bucky's solution solved it - nice. Updated mine above for a little history and in case that doesn't help someone with a different device.

---

### Post by Old Jimma on 2016-06-20
Hi All:

Bucky Ball's suggestion worked perfectly!  By adding exfat-utils and exfat-fuse from the repos I could 

1) simply plug my android into my Ubuntu desktop... and nautilus saw the android and the SD card, and

2) remove the card from my android, insert it into an sd card reader, and add music directories.

Both worked easily!

I did not need to do the things the Fu suggested.

However, I am greatful for the Fu's reply.... The Fu has ALWAYS been extremely helpful to me on the forums!

Many thanks to all!
Sincerely,

Aging Old Jimma

---

### Post by Bucky Ball on 2016-06-20
Excellent news and thanks for marking a solved. ;)

---

