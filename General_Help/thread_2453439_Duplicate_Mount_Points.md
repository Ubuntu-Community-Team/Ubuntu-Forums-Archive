---
title: "Duplicate Mount Points"
date: 2020-11-10
forum: General Help
---

### Post by fozziebear on 2020-11-10
I am a Linux Newbie but slowly finding my way around Xubuntu 18.04. However I seem to have created duplicate mount points on my second hard drive. 
I have a 320Gb hard drive dev/sda1 containing the file system and a second 500Gb hard drive dev/sdb1 used for user data. Some how I have created two mount points for this second drive. This only shows up when using a Sudo session of Thunar. the two mount points are diplayed in the file system as ***media/Data ***and*** media/Data1 ***the latter of which is visible under my normal login profile.

What I am unsure of is whether the contents of the sub-folders on the mount point ***media/Data*** is the same as ***media/Data1*** or if indeed these are completely separate files (hidden other than Thunar as Sudo) 

Is there a way to remove the second mount point and preferably rename the remaining mount point to Data instead of Data1
Its not a big deal but I am having occasional issues with the Hard drive dev/sdb1 not auto mounting at boot which is necessary for my Plex library.
Many thanks
Fozzie

---

### Post by TheFu on 2020-11-10
First, dev/sda1 and /dev/sda1 are different.  You want /dev/sda1 - using the absolute path, not a relative path.  Windows has the same PATH ideas, so this shouldn't be anything new.

The same for /media/ vs media/ ... stay with absolute paths - /media/ or it won't work.

/etc/fstab is where permanent storage mounts belong.  If you fish for "ubuntu fstab", you'll find a how-to guide.  The problem with these guides is that they have to handle every possible situation - or at least most of them - so they are more complex than strictly needed.

Being new, you've probably never considered which file system to use.  On Windows, there are 3 - NTFS, exFAT and FAT32.  On Linux, there are 25+, including those 3.  But on Linux, you should avoid using NTFS or FAT or exFAT whenever possible because they don't support Unix permissions.  There are times when that is absolutely critical and NTFS will not work, period.  For data-only stuff, not programs, so things like music and videos, NTFS isn't THAT bad, but if you want permissions to work, don't use NTFS.

So ... after you get the storage mounted in the fstab, those locations won't show up separately in any file manager.  I'm assuming you are talking about some file manager showing the mount locations?

BTW, please don't use GUI programs with sudo. That is the way to madness and bad things can easily happen. GUI programs that need elevated permissions should ask for those permissions.  sudo abuse is a real problem for newbies. After a few weeks abusing sudo, you'll likely need to reinstall.

So ... all of this stuff - plex, sudo, mounts, lead to Unix file and directory permissions, which you have probably avoiding understanding.  Those are central to all Unix system security.  Fish for "ubuntu file permissions" to find a tutorial that you can work through.  Get over the "no GUI" stuff and spend 30-45 minutes learning this stuff. It is elegant and very clear. Spend 15 minutes after that with 3 user accounts in 3 terminals with 2 groups and try out every possible permissions, mixing and matching the users, groups and learn which can access files in the current directory, subdirectories and which accounts cannot. This 45 minutes of effort will save you hours, days, weeks, months of frustration.

So ... back to the fstab and mounting file systems. We mount file systems, not partitions, not drives.  File systems. That is how Windows works too, BTW. They are just incorrect with terminology.

The fstab file uses 1 line for 1 mount.  Line wrapping is not supported. Mount settings must all be on 1 line, period. Different parts of that line are separated by 1 or more spaces.  The mount options part, cannot have any spaces at all because a space is a separator in the fstab config file. Having an extra space is a common mistake.

If you want the exact fstab line to be used to mount, post the UUID (blkid command) and the file system type, so we can help. Every file system has a unique UUID - well, it is unique to the system, so that is sufficient.

There are many subtle considerations with mounts that can be addressed later.  For example, I'd never mount USB storage in the fstab, only SATA, eSATA, SAS, or Infiniband connected storage - and perhaps iSCSI storage. Those are topics for another question.

---

### Post by TheFu on 2020-11-10
BTW, this new article about exFAT performance: [https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1](https://www.phoronix.com/scan.php?page=article&item=exfat-linux-59&num=1) on flash media. Best to use f2fs instead until the kernel version of exFAT actually gets into mainstream distros sometime in 2021.

---

