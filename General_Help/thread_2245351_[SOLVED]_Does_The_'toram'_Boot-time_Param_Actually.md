---
title: "[SOLVED] Does The 'toram' Boot-time Param Actually Work ?"
date: 2014-09-22
forum: General Help
---

### Post by TheJetman on 2014-09-22
I have remastered several distros, but I currently use just two: PCLinuxOS and Lubuntu 14.04.  What I mean is that my multi-distro DVD/UFD only has two custom remasters.  Actually, I have access to a couple more: Parted Magic and Knoppix.  Okay, I sometimes like to boot a distro to RAM and just use the PC like that for several days.  Persistence of profile info hasn't been important to me in this mode.

I recently tried (today) adding 'toram' at boot-time, replacing the 'splash' option and while it ***appears*** to work, unlike Knoppix, Parted Magic, and PCLinuxOS, some programs malfunction, as in they simply crash (vanish) almost immediately after launch.  My other distros copy the compressed filesystem into RAM and work flawlessly (in either mode) hence I expected the same from Lubuntu.  Perhaps the errant behavior is due to my remastering system, Remastersys ?

```

APPEND file=/cdrom/lubtool/preseed/custom.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/lubtool/casper/ initrd=/lubtool/casper/initrd.gz quiet toram splash --

```

BTW, is there some **up-to-date** master list of these boot-time params ?  Thanx....

PS:  GOOGLEing this param hasn't produced useful results....

---

### Post by TheJetman on 2014-09-26
I removed the 'splash' and 'quiet' boot-time params and discovered the TRUE problem !  There is a message that reports that the size of the image > available RAM.  Unlike other distros, Ubuhntu copies the **entire** media instead of just the compressed filesystem, so this will **never** work on my multi-distro project.  At least I know what went wrong....

---

