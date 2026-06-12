---
title: "Testing the FS-Driver to read/write ext3 from WinXP"
date: 2007-01-16
forum: General Help
---

### Post by Dominicus on 2007-01-16
Hello community,

I'm starting this thread to get your inputs and share my experiences testing the [FS-Driver]("http://www.fs-driver.org").

The purpose of the driver is to get ability to read/write to an ext2 or ext3-formatted partition from WindowsXP (or other Windows versions).

The recommended path for creating shared read/write Linux&Windows partition is to format as FAT32.  However, if the space also needs to hold files >4Gb, then you need something else.  You can setup the partition as ext2 or ext3 and install fs-driver in XP, or you can setup as NTFS and install ntfs-3g in Ubuntu (still beta at this time, but I [read ]("http://boff.wordpress.com/2007/01/13/readwrite-to-fat-and-ntfs-partitions/")is a viable fallback).  

So far I've collected the following advice when using the FS-Driver:
[LIST]
[*]Expect to have to fix this disk once in a while (i.e. after Windows crashes)
[*]Don't use the driver to access partitions where you expect to enforce permissions (as it does not do permissions!)...Corolary:**Never setup access to your ext3 / (root) from Windows using this driver!**
[/LIST]

I'm in the process of setting up a dual-boot system and I will be setting up a separate partition to test this driver and try to get a sense of performance and crash-recovery.  If you already have experience or inputs for me, these are welcome.  Here are some of the things I'm curious to learn:
[LIST]
[*]How much of a performance hit do you incur reading/writing using this driver to ext3/ext2  in WinXP vs read/writes to native NTFS?
[*]How much effort is involved recovering the drive after the inevitable XP crash?
[*]Are there any benefits formatting as ext2 vs. ext3 (the driver is actually an ext2 driver)?
[*]Is this viable as a storage solution for Windows-generated large compressed files?
[/LIST]

If you're wondering why I'd even try setting this up, you can check my other [rant]("http://www.ubuntuforums.org/showthread.php?t=338675").

Just a couple more days until my new hard drive is delivered.....tick tock...Thanks in advance to those who choose to add their thoughts to this thread.

---

### Post by meng on 2007-01-16
I use the fs-driver, but I don't use Windows that much on my dual-boot system. Therefore, I can't speak meaningful about performance or crashes. I use ext3, it's just ext2 with journaling anyway. Basically it works, but I don't try to strain it!

---

### Post by diegocanal on 2007-01-17
I set up a dual boot system XP-Ubuntu three months ago using FS-driver on a ext3 partition. I use it as My Documents partition and the point was to be able to share files  between both OS.  I am a XP user trying to migrate to linux so I use XP mainly. I will try to answer some of your questions based on my experience:

    * How much of a performance hit do you incur reading/writing using this driver to ext3/ext2 in WinXP vs read/writes to native NTFS?
     - I would say the  reading/writing performance is as good as in a NTFS partition. I use a SATA drive with four partitions: one NTFS for XP , one ext3 for Ubuntu, one ext3 for My documents/home and one for swap. I have never run a benchmark test but that is my impression. Notice that you can not defrag an ext2/3 partition  from windows, but from my experience you will not need to do it.

    * How much effort is involved recovering the drive after the inevitable XP crash?
    - It has happened to me twice and, being an absolute beginner in Linux I coped with it, I just had to unmount the partition, run fsck and mount it again.

Have a look at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

---

### Post by Dominicus on 2007-01-17
Here is the software I intend to run to benchmark the fs-driver overhead on access speed:
[http://www.passmark.com/products/pt.htm](http://www.passmark.com/products/pt.htm) (30-day full-featured trial period).

Will you run this on your NTFS vs ext3-over-FS-Driver and post results?  I'd be interested to see how this comes out for your SATA drive (since I only have IDE/ATA100).

It runs big file read/write as well as random access to small files (this is the most demanding one, and why fragmentation can cripple a PC...my drive's transfer speed was 8x slower on random, small-file access!).

I downloaded it to test the impact of CPU upgrade and Video Card upgrade.  One thing I noticed was hard drive performance remained flat after CPU upgrade (1.5 to 2.6GHz) so certainly my PC is at point where hard drive access speed can bottleneck certain apps, thus my concern with performance hit from FS-Driver on apps that feed from HD (i.e. video editing, games, hard-drive backups). 

I'm still waiting for my new drive to be delivered!

Cheers!Dominicus

---

### Post by Shay Stephens on 2007-01-17
I used this last year for a time.  At first it worked, but over time it started corrupting the ext3 drive.  So I uninstalled it and the problem went away.  It may work technically, but in a practical way, it was not stable enough for me to use.  I don't recommend it based on my experiences.

---

### Post by Dominicus on 2007-01-17
For completeness. I should point out there's an alternative to ext3/FS-Driver.  [This]("https://help.ubuntu.com/community/MountingWindowsPartitions") documents how to set up common read/write filespace between Windows and Linux using NTFS file system and the beta ntfs-3g application (available from Edgy repos).  May want to give this a try first or as fallback.
Cheers!Dominicus

---

### Post by diegocanal on 2007-01-19
Hi!

It´s amazing! I´ve just run "Passmark´s Performance Test 6.1" and here are the results. Look at the attachment [ATTACH]23419[/ATTACH]. Both partitions belong to the same SATA drive.  The EXT3+FS-driver partition gets a Mark Rating 132% higher than the NTFS partition. The test was run on XP. You´ll find the biggest difference (huge!) on the "random seek + RW" test, getting an  increase of 12875% in performance on the EXT3 partition compared to the NTFS one.

Extracted from Performance Test Help: "How full the disk is and its cluster size can affect the read / write performance of a disk. The position of the test file on the disk (inner cylinder or outer cylinder) can also affect the performance. The only way to avoid this problem is to only test newly formatted disks that have the same cluster size."

I don´t know if this Test is reliable enough in this situation, as partitions have different size and have no idea what the cluster sizes are in both of them. And sorry, I don´t feel like formatting them now.

NTFS partition´s total size is 60 Gb with 38,3 Gb of free space (64%).

Ext3 partition´s total size is 160 Gb with 129 Gb of free space (80%).


This brings something up to my mind: should every windows user have an EXT2/3 partition and FS-driver instead of an NTFS one, in order to improve HD performance? plus it would not be necessary to defrag.

Cheers

---

### Post by brandonjp on 2007-09-16
Just thought I'd add my experience I've got a Ubuntu / Windows XP dual boot system.  I started from scratch by partitioning the Hard drive to allow for Windows install, Ubuntu install and the rest a larger partition as my "TANK" for media, documents, etc.  The TANK is formatted ext3 and I've been using the fs-driver.org IFS driver for it in Windows and have had absolutely no problems with it.  I actually have ended up running Windows 80% of the time now (because I added a 2nd monitor and can't get ubuntu to display right)

I even us the ext3 TANK for recording audio files to, video editing and other tasks that are rather important to have a reliable drive.  It's been very nice because my linux partition can easily access the files and Windows has had no problems with it at all.  My only concern now is that since Windows has been writing to the drive, that it might need defragged??

--bp

---

### Post by darrengoddard on 2008-01-02
i'm just entering into the murky world of dual booting.  i've recently added a second drive with winXP (ntfs).  linux mint finds the drive without any problem thanks to ntfs-3g but i'm having all sorts of problems finding the linux drive (standard mint installation (ext2/ext3))

i've been looking at a couple of programs that i can run in windows: fs-driver.org and explore2fs but neither work.

before i go into detailed explanations about what exactly isn't working, is it the case that these programs only work on partitions within the same drive - in other words will they not even look to a second hard drive?  or is there a solution to this waiting for me out there in search engine world.

please forgive my ignorance of these matters and accept my thanks in advance

darren

---

### Post by dannyboy79 on 2008-01-02
they'll see any drive. did you install the fs-driver program in windows? did you follow the directions for installation? read the fs-driver website for faq and helpful tips. It does work, I use it.

---

### Post by dagnabit dang doohickey on 2008-01-02
There's another option for accessing your files from ext3 filesystems within Windows: [Linux Reader]("http://www.diskinternals.com/linux-reader/")
It operates in read-only mode, so it won't replace [Ext2 IFS]("http://www.fs-driver.org/"), but when grabbing a file is all you need to do, this is a safer way of going about it.

---

