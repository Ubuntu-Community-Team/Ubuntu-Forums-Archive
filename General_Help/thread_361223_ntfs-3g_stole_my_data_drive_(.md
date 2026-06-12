---
title: "ntfs-3g stole my data drive :("
date: 2007-02-14
forum: General Help
---

### Post by predator on 2007-02-14
It appears as if my playing around with ntfs-3g driver under Kubuntu Edgy 6.10 has resulted in it "stealing" my main data partition (an NTFS volume), with all of my movies, downloads, mp3, etc on it (the good stuff) :( 

It's fine under kubuntu and I can read all the files (thankfully), however when i boot back into ye-olde XP.. I receive a "drive D: is not formatted, do you wish to format this drive?" .. (god no!)

I remember about the last think I did was copy a bunch of other files from another NTFS volume onto that one under Kubuntu. I believe the original volume may have had some errors, as it did display some errors at the time, and I can no longer read them under XP either.

So I was just wondering at the safest way to make sure XP can read it all again?? I can run TestDisk, Gparted, Foremost, etc but just a bit worried they may do more harm than good. I *can* access this ntfs volume under Linux, it just appears that XP has now rejected it :(

Is this an evil ploy to get me to stay on kubuntu permanently :p

---

### Post by logos34 on 2007-02-14
try running **ntfsfix** (it's in the **ntfsprogs** package)...Post back with your results.

---

### Post by givré on 2007-02-14
predator, which version of ntfs-3g do you run :
```
ntfs-3g -v
```

---

### Post by predator on 2007-02-14
version is thus: ntfs-3g v20070920-BETA - Third Generation NTFS Driver

I type 'sudo ntfsfix /dev/hdb1/' on the drive

> Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/hdb1 was processed successfully.


Unfortunately I just rebooted then, and no change in XP :( If I try and run chkdsk back under XP I get...

> C:\Documents and Settings\gfresh>chkdsk d:
The type of the file system is RAW.
CHKDSK is not available for RAW drives.

I was thinking maybe if I use gparted to resize the volume it may rewrite all the partition information, and things may go back to normal.. however I am also concerned that this could result in massive data loss if there is a major problem.

---

### Post by cmost on 2007-02-14
I don't mean to sound cynical, but, you guys will never learn.  I don't care what the developers of all these nifty NTFS tools tell you, writing to NTFS is NOT stable under Linux.  NTFS is a proprietary file system; not open.  As long as it's not open, these sorts of problems are going to keep biting folks in the bum, however infrequently.  Furthermore, why one would "experiment" on a drive containing many gigabytes of valuable multimedia files without first backing the volume up is beyond insane.  It simply defies common sense.  I don't mean to sound like a jerk, I'm only stating this because I too, learned the hard way once upon a time.  If it comes down to a Windows format versus an open format, the Windows format is going to give you the most trouble.

If you want to share your data between Windows and Linux, a reliable method (using open specifications) is to format the drive as Ext2 or Ext3 (will be treated like Ext2) and utilize the Ext2 Installable File System For Windows (get it here: [http://www.fs-driver.org/](http://www.fs-driver.org/))  It provides Windows with full read/write access to Linux Ext2 (or Ext3) volumes.  This little driver is nice.  I carry it around on my USB keys in the event I need to access one of my external Ext3 drives on other Windows computers.  If you like the ReiserFS file system, which is very good, then you're also in luck as there's a reliable driver for Windows.  It's known as rfsd:ReiserDriver.  Development on this driver has been infrequent, but it's still a useful tool.  Grab it here:  [http://rfsd.sourceforge.net/](http://rfsd.sourceforge.net/).  Googling may reveal other equally effective solutions.  Good luck.

---

### Post by szaka on 2007-02-14
> **cmost said:**
> I don't mean to sound cynical, but, you guys will never learn.  I don't care what the developers of all these nifty NTFS tools tell you, writing to NTFS is NOT stable under Linux.
The problem doesn't seem to be NTFS related even if the used driver is terribly outdated. The files can be read on Linux but Windows says the filesystem TYPE is unkown, so it doesn't even try to mount the relevant partition. Why? There can be many reasons. For example the partition table is corrupted (unrelated to NTFS), or the drives were rearranged for some reason so it's not D: but something else (unrelated to NTFS), etc.

Predator, what's the output of fdisk -l? Did you use gparted previously? It has serious problems which could make the partition table damage you have (also unrelated to NTFS, it happens with FAT32 too).

---

### Post by predator on 2007-02-14
> If you want to share your data between Windows and Linux, a reliable method (using open specifications) is to format the drive as Ext2 or Ext3 (will be treated like Ext2) and utilize the Ext2 Installable File System For Windows (get it here: [http://www.fs-driver.org/](http://www.fs-driver.org/)) It provides Windows with full read/write access to Linux Ext2 (or Ext3) volumes.

yes, I am leading towards that option, and have got that working under XP.. but obviously moving towards that requires a lot of reconfiguring, moving files around, and many hours of work. It's not something I'd just tackle right away after having recently shifted to Ubuntu. 

Also, while ideally, yes, I'd have a backup of everything.. but having a spare 200gb drive, etc sitting around just to backup every single thing is not always practical, and expensive. I just have to deal if a problem like this occurs (like many people) 

I know there are warnings, but if you try something, you obviously expect it to work fairly well unless it's very beta. 

> Predator, what's the output of fdisk -l? Did you use gparted previously? It has serious problems which could make the partition table damage you have (also unrelated to NTFS, it happens with FAT32 too)

no I haven't used gparted, or mucked with the partition tables I don't think.. will have to check fdisk and see what it says.. XP can 'see' the partition, not read it, it thinks it's type RAW.  As I said, it doesn't even really appear to be a major problem in Ubuntu's behalf, the data is still all there - I was even playing back some movies last night without any problem. 

I guess tonight I'll start backing up what I can from this partition and running some kind of repair process and see what happens.

**UPDATE: Fixed! after trying ntfsfix again, I rebooted into XP, which proceeded to do a chkdsk before startup. This fully allowed my XP to "see" my XP drive.. and now all is well.**

---

### Post by szaka on 2007-02-15
There are several signs that you have hardware problem. Please send the output of chkdsk according to this: [http://en.wikipedia.org/wiki/CHKDSK#Viewing_results](http://en.wikipedia.org/wiki/CHKDSK#Viewing_results)

---

