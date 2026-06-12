---
title: "System Backup Solution (mainly for quick rebuild times)"
date: 2007-04-10
forum: General Help
---

### Post by louish on 2007-04-10
Hello All.

I'm looking for a solution to backup my Laptop (Ubuntu 6.10).  And what I want to use is my NAS box.  I currently have a 2Tb Buffalo Terastation.  Which has Gigabit Ethernet, and supports smb and ftp.   I current run only two partitions "/" and "/home".

I've looked at a few, (keep, sbackup, grsync) and each has one problem or the other.  So far for speed and ease of use, I was happy with sbackup, but when I have an 8.1GB tgz.  Trying to get one file or directory proved to be a real pain.

Since I tend to play on my laptop far to much, I would like to find something that will help me protect myself from well...  me!!!

I guess my looking for is a solution that if I would happen to delete lets say...  /usr/bin or /sbin that I could just go and restore what I have from the nas box...  Or that I could take a "fall back" image if an upgrade completely buggered my system, etc etc.

Tia
Louis

---

### Post by spankymasterc on 2007-04-10
umm here check this out!

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

its easy... this is how i have mine backed up ::cheers::

---

### Post by laidback on 2007-04-10
Don't know what a nas box is but I use a USB hdd and Gparted to backup my system, as a result I have all backed up files available 'on line' as it were. I can read them just as if they were within my regular system.
Post message if you would like more info.

---

### Post by louish on 2007-04-10
Yes,  Please explain.  I'm not sure what/how you would "backup" using gparted?

---

### Post by laidback on 2007-04-10
You backup the entire disc. Gparted has a copy button.
I have a 250Gb USB hdd which I have partitioned for a variety of uses, one of which is the backups. I have 3 partitions of equal size to my daily used hdd (approx 10Gb). These are used in turn for the backup sequence, previous unwanted copies are over written with the latest version, keeping 2 copies as they were, the last and previous one. As you cannot "copy" a mounted partition I use the Gparted Live CD to boot from (The Ubuntu Live CD would do just as well as it has Gparted on it). From Gparted I can organise the partitions, reformat, create new ones, delete etc as needed. 
I instruct Gparted to copy my main hdd onto the USB hdd choosing the appropriate partition for this backup (as above). It takes approx 24mins for my copy. Gparted's copy will be the same size as the original partition regardless of how much space is actually used up. This is why you need backup partitions the same size as your orginal hdd, too small and things go wrong. I actually have them slightly larger than the original (+ 1Gb).
The copy really is a copy, you can view it, navigate it and access all files, it's copied the entire disc, including hidden files. I've even used the copy to create a clone hdd which I then put onto another pc, amazingly it booted and I had the original but elsewhere, even my email worked. The pc's had different hardware but were of similar types. No fancy 3d video.
So far I haven't come up with any problems with this system, I've been using it for about 3 months now.. I name each backup partition with the date, and have a readme file with info. This file can be added to the backup partition at / level as the backup acts just like any other partition, you can mount it, umount it, write to it, copy from it etc. So I use gedit to create the readme file.

I hope this helps. Post again if you have any other queries.

Kindest regards
Laidback

---

