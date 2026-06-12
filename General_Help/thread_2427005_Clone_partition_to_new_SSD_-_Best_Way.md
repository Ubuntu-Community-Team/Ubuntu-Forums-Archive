---
title: "Clone partition to new SSD - Best Way"
date: 2019-09-16
forum: General Help
---

### Post by mmatzen2 on 2019-09-16
Hi. I currently dual boot win10 and Ubuntu 18. I’d like to clone my Ubuntu install to a new SSD, but without the win partition and wanted to keep the old drive for archiving (old drive is also an equal size SSD). For ease of use I was thinking of just using clonezilla, but wanted to get the opinion of the community. Also, I’ve never used conezilla before, so was wondering if that is even an option (I know there is a straight disk to disk clone option but wasn’t sure about only cloning the partition itself). Any advice is appreciated. Thanks, in advance!

---

### Post by mmatzen2 on 2019-09-16
Also, as note, I guess this would mean the partition would be on (technically) a larger drive since it wouldn’t have win on it; so maybe it is better to say cloning same sized drive but to larger partition is a better way of putting it (maybe).

---

### Post by oldfred on 2019-09-16
If UEFI with gpt partitioning, I am not sure you can clone one partition.
GUID has info in primary partition table, backup partition table & partition that must match. 
And you  cannot have duplicate GUIDs or UUIDs. 
Do not know if Clonezilla can handle that configuration or not.

Often better just to do a new install & copy everything from your normal backup. Good way to confirm that your backups include everything you need as you still have old install to go back to, if something is missed.

---

### Post by TheFu on 2019-09-17
How new to Linux, booting, partitioning are you?  There are many considerations and likely to be tiny issues that someone with experience would recognize immediately, then correct quickly, but someone really new would just get into more trouble over those tiny problems.

First, the physical sector sizes on both disks should be the same.  That's either 512b or 4Kb. If you try to clone between different sizes, it is easy to end up with misaligned sector boundaries which can make performance 30% less.

Really, I'd push for this to be a way to validate your backup and restore process for Ubuntu. Everyone needs a backup and tested restore for their Unix-like systems.

There are two major ways to perform backups
* Images - bit-for-bit
* Files/Directories
Images are best when you have lots of storage and lots of downtime is allowed for every backup. These are slow and huge.
File-based backups can be very efficient, fast, don't need downtime, and only need a little more storage than the original to have many "versions" - I keep between 60 and 180 days of versioned backups for my systems.

Image tools - clonezilla, dd, ddrescue, fsarchiver.  If the original disk is dual-boot, then the target disk needs to be dual-boot too. After the cloning, you can remove Windows, if you like.  The issue is that the boot code expects 2 OSes, in specific locations.  If you are comfortable manually fixing boot issues, then you can backup just the specific partition that you want.  I'd use fsarchiver, booted from a flash drive OS when I go in this direction.

File-based backup tools - rsync, rdiff-backup, deja dup, duplicity, duplicati, rsnapshot, rbackup, sbackup, aptik, back-in-time and probably 50 others, since lots of people will build a tool about librsync and call it the *greatest backup tool ever!*  Each of these tools has issues, but overall, file-based backups make up for the small issues by being efficient on time and storage.  

I use rdiff-backup and file-based backups.  My restore process begins with a fresh installation, so there isn't any problem with booting or old drivers. It also means moving to new hardware works without anything special.  I don't backup any drivers.  Just the 4 things - system settings, data, and personal settings data.  Most of my backups take 2-8 minutes a day for each system.

If you are stuck on cloning everything, use ddrescue. Hope that the partitions aren't misaligned. Clone the entire disk.

If you must clone just 1 partition, use fsarchiver.  You'll need to manually setup the partitions and fix the booting.

If you go with file-based backups, grab /etc/, /home/, /usr/local/ (if you manually install stuff there) and a list of all the installed packages using **apt-mark showmanual**. Then do a fresh ubuntu install to the new disk.  Restore the files from /etc/ that are needed, restore everything from /home/ and /usr/local/, then use the list of manually installed packages to feed into APT and restore them again.  Each part is about 15minutes, worst case.  45 min total.  When you are done, you have a fresh install, on new hardware, with all your settings and all the programs back.

Clear as mud?

---

### Post by mmatzen2 on 2019-09-17
This is fantastic! Lots of helpful info and food for thought. Honestly, I think the route I’ll take is to just backup files and do a fresh install on the new disk. Honestly, the old disk is just going to go into storage until enough time passes where I say screw it and just zero out and use for something else. Anything that is Uber important is on my raid, anyway. I think I was overthinking and just trying to get around having to reinstall some applications, which I have exports of workspaces, anyway. And it’s not like it’s that time consuming to add them to a fresh install. So in the end it makes more sense to just start fresh since I’m ditching windows and never use it (and dedicating the full drive to Ubuntu). Seems like less problems and a more direct approach.

I sincerely appreciate the info you provided. 

Many thanks!

---

### Post by TheFu on 2019-09-18
RAID never replaces the need for backups.  If you don't have 3 copies of files (RAID is only 1), then you don't have a backup.  These forums are full of people with broken RAID arrays trying to recover data.  With a backup, it is easy.  With just the RAID data, it is difficult and sometimes impossible.  

RAID solves 2 issues and only 2 issues.  HA and, perhaps, improved read performance.  It is a bunch of work for those and almost always better off using an array in a non-RAID mode with good backups anyways.  If you use quality SSDs and have good backups, there is little reason for RAID at all these days.  Cheap SSDs are a different problem entirely.  I've had a few of them fail well before  expected.

Backups solve at least 1001 problems.  RAID solves 2.

---

### Post by mmatzen2 on 2019-09-19
Point taken; I should have also mentioned that I do daily incremental backups of my raid to wasabi, so should be okay other than having to replace/rebuild when stuff  inevitably happens.

---

### Post by williammay on 2019-09-20
> **mmatzen2 said:**
> Hi. I currently dual boot win10 and Ubuntu 18. I&#8217;d like to clone my Ubuntu install to a new SSD, but without the win partition and wanted to keep the old drive for archiving (old drive is also an equal size SSD). For ease of use I was thinking of just using clonezilla, but wanted to get the opinion of the community of[COLOR=#000000] [/COLOR][[COLOR=#000000]bigg boss 13[/COLOR]]("http://kasautiizindagiikay.me/category/big-boss-13/"). Also, I&#8217;ve never used conezilla before, so was wondering if that is even an option (I know there is a straight disk to disk clone option but wasn&#8217;t sure about only cloning the partition itself). Any advice is appreciated. Thanks, in advance!

Same question and got the solution.!

---

### Post by TheFu on 2019-09-20
> **mmatzen2 said:**
> Point taken; I should have also mentioned that I do daily incremental backups of my raid to wasabi, so should be okay other than having to replace/rebuild when stuff  inevitably happens.

As long as wasabi captures file and directory permissions and ACLs in addition to the data, it should be fine.  On Unix systems, the permissions are 50% of what needs to be backed up. Without that, restoring will be next to useless, except for media files.

---

