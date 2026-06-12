---
title: "Help with disk maintainance"
date: 2007-05-15
forum: General Help
---

### Post by TheUndead on 2007-05-15
Hello, I'm new here.. my first post, so have mercy:)
Here's the problem: I use Ubuntu Feisty, and i have an iAudio X5 DAP, which has a UMS USB HD interface (30 gb HD).
Ubuntu recognizes it as a media device, and mounts it in /media/IAUDIO/ , whereas windows sees it as a regular USB hard drive (UMS device)
For reasons of the DAP's firmware functionality, it _**must**_ be formatted to FAT32.
How do I maintain (Scan and defrag) a USB hard drive using FAT32 under Ubuntu? 
Please help, because I'm struggling with this one for quite some time now... Thank you:)

---

### Post by bscbrit on 2007-05-15
This is a good question - but I'm not sure that there is a good answer.  I am not aware of any program in Ubuntu that defrags FAT32.  I understand your requirement to keep the drive formatted this way so all I can suggest, until someone with a bright idea comes along, is to continue to use it as you do.  If you notice any serious problems with the drive, copy all the data somewhere else, reformat the drive as FAT32, and copy it back.  Although I understand the problems of fragmentation I suspect that it will not actually cause a continual problem but might, occasionally, benefit from the procedure that  have outlined.

The disk will still be scanned automatically after a specified number of mounts.  (see 'man tune2fs').

On the positive side, this might be a good reason to keep you audio data backed up on DVD / CD or another HD. :-)

---

### Post by TheUndead on 2007-05-15
It doesn't scan it automatically even after 30 (default) mounts, as it doesn't mount it as a disk drive, but as a media storage device or something like that...

---

### Post by bscbrit on 2007-05-16
You can always scan it manually from the command line, or write a script that will do this automatically when you have plugged in the drive.

---

### Post by TheUndead on 2007-05-16
What should I use to scan a FAT32 disk that's not mounted as an HD?

---

### Post by bscbrit on 2007-05-16
A quick search suggests that either fsck.vfat or dosfsck should do what you want.  Run them as root ('sudo fsck.vfat') when the drive is connected as a device (/media/lAUDIO) but before it is mounted. EDIT:  /media/lAUDIO is mounted - you will have to identify the /dev/.... point that connects to it)

I haven't used either command - I don't have any FAT32 partitions.... - but I cannot see any reason why they will not do what you want.

Good Luck

---

