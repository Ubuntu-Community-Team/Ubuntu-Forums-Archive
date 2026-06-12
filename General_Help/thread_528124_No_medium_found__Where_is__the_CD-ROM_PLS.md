---
title: "No medium found?  Where is  the CD-ROM? PLS"
date: 2007-08-17
forum: General Help
---

### Post by Ubunme2 on 2007-08-17
Unable to mount CD-ROM.

Dell Inspiron with Ubuntu 7.04, everything else is fine but it won't mount the CD-ROM.
The CD-ROM works, the operating system was installed from it, it is enabled in the bios, it shows up fine in the CD-ROM drive properties dialog box as a Samsung CD-ROM SC-148F.
yes, there is a CD in the drive.  Yes, I have tried many different CDs both audio and data.  Yes, I have checked the forums and read dozens of similar threads.  Yes, I have tried to mount the device through the terminal, (many different ways) "no medium found", "mount point does not exist" or "permission denied".  Yes I have tried etc/fstab "command not found".  I have also installed "p mount" -hal for auto mount.  All to no avail.
I recycle and donate old computers, have installed Ubuntu on many different computers and never had a problem before.
Thank you all for helping with this terrific operating system.

---

### Post by dabl on 2007-08-17
Is there a mount point for it in /media?  Usually it is /media/cdrom0 for a single CD ROM drive.  Then /etc/fstab needs a line in it to show the /dev/sdc0 device, and the mount point and mount options, something like this:

> /dev/scd0   /media/cdrom0   udf   noauto,users,ro   0   0

---

### Post by Ubunme2 on 2007-08-17
Thank you for your help,

I finally got into:
sudo nano etc/fatab  
and I found:
/dev/scd0 /media/cdrom0 udf ,iso9660 user ,noauto 00

---

### Post by Ubunme2 on 2007-08-17
I also just tried the floppy disk, and it works and shows:
/dev/fd0 /media/floppy0 auto rw ,user .noauto 0 0

---

