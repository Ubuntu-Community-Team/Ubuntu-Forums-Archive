---
title: "Checking a filesystem (ext3) for errors.. need help to see if any files are damaged"
date: 2007-04-17
forum: General Help
---

### Post by billdotson on 2007-04-17
I have a 100GB partition that I use strictly for backup images for my OS installs.  I have one that is a backup image of a clean XP install, one where I have all my stuff installed and a clean install of Ubuntu.  

I went into gparted (by doing sudo gparted.. I installed gparted w/ apt) and told it to resize from 100GB to 60GB (~59GB was all I was using) and it was taking a very long time.. like 20 minutes and never showed any progress.  I  ignored gparted's warning and cancelled anyway.  Since I had those backup images on there I decided to check the filesystem integrity of the partition to see if I had damaged any of those backup images.  

I ran fsck /dev/sdb6,  fsck.ext3 /dev/sdb6, fsck.ext3 -r (I think it was r; if -r is to check for bad blocks then it was) /dev/sdb6 and fschk.ext3 -f /dev/sdb6.   I ran all of these while the partition was not mounted.

All of the commands except the -r anf the -f options gave me the size and :clean and then said how many files were being used.  The -f and -r ones said that the filesystem had been changed and that there was 5.3% non-contiguous files.  In gparted that partition now shows that it is using double the disk space it actually is.

Did I ruin that partition; am I going to have to remake my backup images?

---

