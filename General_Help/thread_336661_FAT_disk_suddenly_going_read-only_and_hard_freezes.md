---
title: "FAT disk suddenly going read-only and hard freezes"
date: 2007-01-11
forum: General Help
---

### Post by grsing on 2007-01-11
This may very well be two separate problems, but I figured I'd post them together in case there might be some link between them.

1. Sometimes (so far as I can tell, only when I'm running BitTornado) a FAT32 disk I have mounted as read-write  will become read-only. I've searched the forums and seen people with similar problems, but no real solutions (besides some people who had bad disks, but this one is pretty new (less than a year) and works fine in Windows; if there's a test I should run to make sure, please let me know).

2. Occasionally (twice or thrice a day) the system will freeze solid (nothing moves, not mouse, not the system monitor applet, nothing).  Ctrl-alt-bksp does nothing, only a manual reboot fixes it.  I haven't been able to find any common denominator with programs running nor with uptime; again, any tests that would be useful would be great.

Here's my fstab, which is probably more useful for problem 1 (the other FAT drives don't seem to exhibit the same phenomenon, but I don't download torrents to them):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows	ntfs	nls=utf8,umask=0222	0	0
/dev/sda1	/media/BIGFAT	vfat	iocharset=utf8,umask=000	0	0
/dev/hda5	/media/HD0FAT	vfat	iocharset=utf8,umask=000	0	0
/dev/hda6	/media/HomeBack	vfat	iocharset=utf8,umask=000	0	0
/dev/hdb5	/media/HD1FAT	vfat	iocharset=utf8,umask=000	0	0

---

### Post by dcstar on 2007-01-12
> **grsing said:**
> This may very well be two separate problems, but I figured I'd post them together in case there might be some link between them.

1. Sometimes (so far as I can tell, only when I'm running BitTornado) a FAT32 disk I have mounted as read-write  will become read-only. I've searched the forums and seen people with similar problems, but no real solutions (besides some people who had bad disks, but this one is pretty new (less than a year) and works fine in Windows; if there's a test I should run to make sure, please let me know).

2. Occasionally (twice or thrice a day) the system will freeze solid (nothing moves, not mouse, not the system monitor applet, nothing).  Ctrl-alt-bksp does nothing, only a manual reboot fixes it.  I haven't been able to find any common denominator with programs running nor with uptime; again, any tests that would be useful would be great.

Here's my fstab, which is probably more useful for problem 1 (the other FAT drives don't seem to exhibit the same phenomenon, but I don't download torrents to them):

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/Windows	ntfs	nls=utf8,umask=0222	0	0
/dev/sda1	/media/BIGFAT	vfat	iocharset=utf8,umask=000	0	0
/dev/hda5	/media/HD0FAT	vfat	iocharset=utf8,umask=000	0	0
/dev/hda6	/media/HomeBack	vfat	iocharset=utf8,umask=000	0	0
/dev/hdb5	/media/HD1FAT	vfat	iocharset=utf8,umask=000	0	0

Assuming the drive in question is the /dev/sda1, then maybe some power management is affecting the USB/SATA connection and the system is dropping back to RO because of it?

It may be worthwhile to disable any power management settings and see if that changes things.

---

### Post by grsing on 2007-01-12
I don't have any power management running (both sliders are set to "never"). Also, I forgot to mention, if I unmount and remount the disk, it works fine (for a while). And yes, it's the sda.

---

### Post by grsing on 2007-01-12
I've also reproduced the problem on another hard disk (HD0FAT in fstab), so either they're both bad (unlikely), or its a different problem.

---

### Post by cnich23 on 2007-02-13
Did you ever find a resolution to the problem?  I am suffering from the exact same issue ....
I converted my extra hardrive to fat from ntfs before I installed ubuntu on my sata drive, after I mount the drive I will receive random freezes

---

### Post by grsing on 2007-02-13
I resolved it one way or another, although I don't remember doing it. I think I wound up reinstalling, actually, but I could be wrong. More recently, I kept having problems with BitTornado, and wound up switching to utorrent, which seems to have mostly solved those problems, so that might fix it, too.

---

### Post by hazza96 on 2007-03-20
I don't have the HDD freezing issue but I do have the "*USB HDD changes to Read Only for no apparent god dam reason and nothing you do will get the system to do what **YOU** want instead of being off with the frigging Vista faires doing what ever the hell it wants*"

This is really annoying, there HAS to be a process running in the background that changes it to RO even though everything else indicates that it **should** be RW.

---

