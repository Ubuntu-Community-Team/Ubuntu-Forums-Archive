---
title: "Install Disk can't find Hard Drive"
date: 2007-12-05
forum: General Help
---

### Post by upsetfuzzball on 2007-12-05
I bought a laptop about 10 months ago that had vista preloaded on it.  After a while I decided vista was really horrible so I backed up my files and formatted the hard drive to install Ubuntu.  

Now I'm trying to install XP on the laptop again, but I can't figure out how to install it.  When I put in the XP disc, it says it can't find any hard drives, but obviously the hard drive is there because I run linux off of it.  

I've tried reformatting (leaving 80gb for linux, 2gb for the swap, and another 80gb either unformatted or as FAT 16 or 32), but I can't format to NTFS (which is what the hard drives on my XP desktop are formatted as) so I can't install XP.  

Any help?

---

### Post by flaggh on 2007-12-05
EDIT: Sorry, bad reply, read your post wrong.

---

### Post by cdenley on 2007-12-05
Why are you asking how to install XP on an Ubuntu forum? It sounds like the XP cd does not include the driver for your SATA controller. You need a Windows driver floppy disk. You can either figure out what SATA controller you have, search for the drivers from the manufacturer and attempt to create a driver floppy, obtain an external floppy drive for your laptop, then choose to install additional drivers from a floppy during the XP setup (assuming the installer will see your external floppy), or you can keep using Ubuntu to avoid problems like these.

---

### Post by upsetfuzzball on 2007-12-05
I'm using ubuntu for almost everything and I like it *way* more, but some games don't run on this OS.  

Anyway, another friend told me that to get the XP cd to find the HD, I have to have a blank partition... no linux format at all.  I can then install linux again on a separate partition after XP is installed.

---

### Post by -grubby on 2007-12-05
or you could format it to FAT32 first just to make sure

---

### Post by upsetfuzzball on 2007-12-05
Yeah, I already tried that (formatting to FAT16 / Fat32... I've tried both).  I'm at work right now, but I'll know if the total format will work when I get home in an hour or so.

---

