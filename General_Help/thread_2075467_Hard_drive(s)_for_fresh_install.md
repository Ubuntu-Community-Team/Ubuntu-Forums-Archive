---
title: "Hard drive(s) for fresh install"
date: 2012-10-23
forum: General Help
---

### Post by geomcd1949 on 2012-10-23
Decided to build a computer. Was going to install Ubuntu on a 1TB HDD (which I've done three or four times before). I foolishly allowed myself to be persuaded to also buy a 256GB SDD, and install both in the computer. The parts are in the mail. It now occurs to me that installing Ubuntu on a machine with two hard drives is way above my skill level. 

Am wondering if there is a tutorial that explains how to install Ubuntu on a computer with two hard drives, and also discusses the virtues and disadvantages of the various ways the system can be configured. I'm new to Ubuntu, and have only a vague idea of how the OS works, and what the requirements are for having two drives. I've Googled the problem for a week now, but most discussions center around dual-booting with Windows, and don't discuss the simpler problem of two drives only in Ubuntu.

Thanks!

~George

---

### Post by mag1strate on 2012-10-23
Is this what you are looking for? You would be looking at the RAID section which is at the top.

[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

### Post by chilisastry on 2012-10-23
George, Pnstalling with two (or more) drives is just as simple as with one drive.

During installation, at the step where you must specify where to install Linux, ie the partitioner, you probably created partitions on a your lone drive in the past.  Now you will see all the drives (including USB drives if supported by your BIOS) in the computer.  The drives will be listed as /sda, /sdb, /sdc, /sdd, etc.  You cna partition the drives as you wish.  The partitions within each drive (assuming msdos partition table) will be listed as /sda1, /sda2, etc, /sdb1, /sdb2, etc, /sdc1, /sdc2, etc. and so one.  Within a drive, Primary and Extended partitions will be numbered 1-4, and logical partitions will be numbered 5 and above, so /sda4 will not exist if there are only two Primary partitions and one Extended partition (containing one or more logical partitions), for example, on /sda.

Just select which partitions you want to use for which mount points (eg, swap, /boot, /, /home), and go your merry way with the installation.  Will be a breeze.

---

### Post by geomcd1949 on 2012-10-23
Chilisatry,

Thanks very much for your reply.

I'm looking for a tutorial or other extended explanation that would include discussions of things about which I know nothing, such as, for example, swap, boot, partitioning of drives, and the difference between logical and extended partitions. Am also looking for discussions of the advantages of using more than one hard drive, and what options are presented when two drives are installed. You say that I should "just select which partitions you want to use for which mount points," but I don't have any information that would be a basis for making those selections. I bought the book, "The Official Ubuntu Book," but that doesn't address the questions. 

I don't mind experimenting, which is as good a way to learn as any, but I would like to gain at least a rudimentary understanding of what I'm trying to do. Any suggestions on how to find this information is greatly appreciated.

Thanks.

~George

---

### Post by bab1 on 2012-10-24
> **geomcd1949 said:**
> Chilisatry,

Thanks very much for your reply.

I'm looking for a tutorial or other extended explanation that would include discussions of things about which I know nothing, such as, for example, swap, boot, partitioning of drives, and the difference between logical and extended partitions. Am also looking for discussions of the advantages of using more than one hard drive, and what options are presented when two drives are installed. You say that I should "just select which partitions you want to use for which mount points," but I don't have any information that would be a basis for making those selections. I bought the book, "The Official Ubuntu Book," but that doesn't address the questions. 

I don't mind experimenting, which is as good a way to learn as any, but I would like to gain at least a rudimentary understanding of what I'm trying to do. Any suggestions on how to find this information is greatly appreciated.

Thanks.

~George

First things first, you most certainly DO NOT want to attempt configuring 2 dissimilar in sized drives for RAID.  

You can use the SSD drive for the Linux OS (/) and the larger HDD for your data (/home).  You could alternatively; create 2 partitions on the HDD and mount 1 at /home and the other at /var.  This now has most of the volatile (changing) data on the HDD.

There is no one monolithic guide to the information you  want.  Part of it is at ```
man fdisk

man parted

man mkfs
```

The question about logical vs extended is more about how many partitions you are going to need.  Originally you could only have 4 partitions.  The extended partition overcame that.  You can have more than 4 partitions inside the 1 extended partition.  It appears that the newest installer creates 1 logical partition to boot from and an extended partition that you can add your additional partitions.

The best thing to do is to think out what you want (or ask here).  Then ask about what you don't understand.

The installer will ask questions but you really should know what you want to do beforehand.  The first question will be:  Do you want to install on one disk automatically (guided I think is what its called) or manually.  If you are going to mount the HHD to the SDD's file system (@ /home and/or /var), this is what you want.

If you don't mind reinstalling, I would start with partitioning the HDD into 2 partitions while installing Ubuntu to see how it works.  I would wait to use the SDD until you were comfortable with installing.  Too much reformatting and installing is not really good for this device.

The most basic setup for SDD/HDD would be ```
SDD = /  (The OS)
HDD = swap
HDD = /home (your data mounted /home)
```

---

### Post by chilisastry on 2012-10-24
George,

I don't know any documents that will give you the knowledge you want to gain - but then, I am not well-read.  I gained my knowledge in the school of hard knocks.

I'll give you some basic pointers, and you can then think up scenarios and advantages for yourself.  Not too difficult; just common sense is needed.

There are two basic advantages of using multiple drives: minimizing seek operations, and increasing data reliability through RAID.

First, about partitions.  A disk can be partitioned into up to 4 top-level (Primary and Extended) partitions (assuming an msdos partition table).  An Extended partition is a container that can contain many (sub-)partitions; the partitions within an Extended partition are called Logical partitions.  Extended partitions are an artificial construct needed because (in an msdos partition table) there can be at most 4 Primary-level (or top-level) partitions, and if you want to have more than 5 or more partitions on a disk, you must place some of those partitions under one of the 4 top-level partitions.  A Primary partition is a top-level partition that does not contain any (sub-)partitions.


Now for multiple-drives: one advantage of having more than one drive is that seek operations can be minimised, and can be performed in parallel.  In its simplest form, view a drive as a CD, with information stored in concentric circles ('tracks').  Each circle will be divided into sectors.  To read (or write) data to a sector, the read/write head (a sensor) must be mechanically moved to the corresponding circle, and wait for the spinning disc to bring the sector of interest to the read/write head.  The disc spins continuously very fast (5400 rpm - revolutions per minute - or 7200 rpm, typcally), so every sector in a circle can be read quite fast.  But moving a (r/w) head from one circle to another concentric circle (from track to track) - a 'seek' operation - requires start-stop movement which is quite slow, even to move to an adjacent track, and slower still when having to move from an inner track to an outer track.  When reading and writing data, it helps if seek time can be reduced.

If you have two drives, you can, for example, store applications on one drive and data on another drive; when accessing (r/w) data, the (r/w) head on the applicaton drive does not have to change tracks, and hopefully, the next time you have to read an application, the seek time will be minimized.  More importantly, when reading (or writing data on one drive, you can simultaneously do a seek to read an application on the other drive.  The resulting increase in performance can be quite pronounced if you can plan your data layout.  For example, if your /home directory is on one drive, and your /usr directory is on another drive, copying a file from /home to /usr will be much faster than if both /home and /usr are on the same drive.  Database systems do this type of optimizing a lot: they store different tables on different drives so you can get data from different tables very quickly.

If you have ever used the Disk Defragmenter in Windows, it tries to place all the parts of each file (makes the file contiguous, or non-fragmented) on consecutive sectors and neighboring tracks, so that reading the file will require a minimum of seek operations and seek time.

I always have my SWAP partition on a different drive than my / (filesystem root) drive, so my swap operations are always very fast.  Even in Windows, I place my pagefile in a partition on a different drive than my OS and my data; my pagefile partition is just big enough for the pagefile and nothing else (just like the swap partition in Linux!).

In this context, note that when you partition a drive, all the partitions are on the same drive, and seek operations are required to read from different partitions on the drive - quite slow.  Copying a file from one partition to another on the same drive will be quite slow - you can actually see the difference in the times required by copying a large file (like a 4 GB DVD iso image) between partitions on the same drive, and between partitions on different drives.

Next advantage: RAID and data reliability.  Other replies in this thread give you some references that you can read.  In its simplest form (easy to understand), consider having two identical drives, and read and write the same information to each drive each time.  The drives are said to be 'mirrored', that is, each track (all the sectors in that track) on a drive is an exact copy of the corresponding track on the mirror drive.  To read a file, for example, you will read the file from each of the two drives.  If both return the same information, then the data can be considered reliable.  If there is a difference, it means one of the drives (or both!) has failed, and you cannot trust the data.  If you think about it (ie, use common sense) you will realize that it is not necessary to have two drives; you can use two partitions of the same size and mirror the data; the two partitions can even be on the same drive!  If one of the partitions becomes defective (develops error sectors, for example), mirroring will catch the errors. Software RAID implementations do all the work of duplicate writing to the mirrors, and comparison of the reads from the mirrors.  But software implementations are quite slow, hardware-supported RAID implementations (usually called RAID controllers) offer much better performance.

RAID is a much more complex topic.  There are RAID levels from 0 to 5.  RAID 1 is mirroring.  RAID 5 uses many more disks than two, and uses error-correcting-codes to correct read errors so you can determine if a drive in the RAID collection is failing, but continue to use the (corrected) data for immediate use.  Conceptually, you could use 39 disks to store 32-bit data (plus 7 parity bits) and the double-error-detecting, single-error-correcting Hamming code (with an complex hardware RAID controller) to perform quite reliable data processing regardless of occasional data errors.  You can even replace a failed (or failing) disk drive with an empty disk drive (called hot-swap), and the new disk drive will gradually get filled with the correct data!  There is a lot of RAID support in Linux, and you should use it to store important data, like customer information.

Finally, the Linux filesystem.  / is the root for the filesystem, which is tree-structured; this means all directories and sub-directories branch out from the root (like a tree).  /usr/lib/bin is a path from the root and specifies which branches to take to reach the node.  Note that it is NOT necesary for /usr/lib/bin to be on the same drive or partition as /, or /usr or /usr/lib.  You can take any partition and 'mount' it as /usr/lib/bin; all the files - and directories and sub-directories - under that node will be in that partition (unless you also mount another partition under this one, eg, at /usr/lib/bin/myown).  Note that if you create a directory called George under /usr, the node /usr/George will be created in the same partition as /usr.

So / can be on one partition, /boot can be on another partition, /var can be on a third, /var/lib can be on a fourth, /home on a fifth.  And all the partitions can be on any drive, not necessarily on the same drive.  You specify this as the 'mount point' for each partition when installing Linux.

You can also mount a partition at a mount point when running Linux, after installation - read about mount, umount, fstab and mtab in the Linux documentation if you want to understand this.  Note that if you mount a partition at a mount point, any data that was present there previously will no longer be accessible, until you unmount the new partition from that mount point.  In the prior example, you may have data stored in /usr/George (such as your resume or a list of your family members).  If you mount another partition at /usr/George, your resume will be hidden by this new partition and is no longer accessible, until you unmount the partition at /usr/George.

Specifically, /boot is just a directory that contains the operating system files, and the loader will look for these files in the /boot directory, to load the operating system during power up or restart.

swap is more complicated.  You must understand the concept of virtual memory to understand swap.  Suppose your computer has 1 GB of memory, but you need 2 GB of memory to run all the various applications you want simultaneously.  If you have 2GB (or more) of swap space (swap partition on Linux, pagefile in Windows), the computer will make your 1 GB of memory look like you have 2 GB of memory.  Performance will be slightly slower than if you really had 2GB of memory, but the performance will be sufficiently reasonable that you may not even notice the difference. That is the 'simple' explanation; if you want the 'detailed' explanation - very technical - read up about virtual memory, paging and segmentation in a good book on computer architecture.  This is a very old technology created at MIT in the 50's/60's because memory was very expensive and most computers (mainframes in those days) had only 16KB or 32KB of memory!  A lot of today's computer architecture technology was developed at MIT in those days.


OK.  This is a lot of information; actually, fundamental principles.  If you fully understand these principles, you can handle any situation with multple disks and with Linux directories (mount points).  All it requires is common sense from here.


Now, my friend, I have to go.  But contact me directly at iitm07-craig at yahoo if you need more information (only George, please.  All others will be ignored, so please do not spam).

---

### Post by chilisastry on 2012-10-24
Bab1 is absolutely correct in his recommendations.  [Thanks, Bab1.  I did not know that /var has volatile data.]

First, depending on your RAID controller, it is best to have identical disks in your RAID array.

Second, HDD (Hard Disk Drive) and SSD (Solid State Drive) have significantly different characteristics.  HDDs can tolerate far more write cycles than SSDs; with excessive writing and re-writing on the same region of an SSD, that region will start to develop failures ('bad sectors').  SSDs do not have any mechanical movements internal to them, so there is no 'seek' time, and speeds of silicon chips can be much faster than even a 7200 RPM hard drive.  So, intrinsically, SSDs are much faster, both for writing and for reading of data, than HDDs, but tend to develop failures if written to too often.  ['Too often' is a very loose term; actually SSDs can handle hundreds of thousands or millions of write cycles over their lifetime, but HDDs can probably handle billions or trillions of write cycles in their lifetime.]

Because of these characteristics of SSDs, it is best to use them to store data which will not change very frequently, and which must be read very fast.

Bab1 recommends - correctly - storing the operating system files and applications files on the SSD (the / node of the file system) AND storing the files that change frequently on a HDD (swap, /home and /var; /tmp is another such candidate).  Alternately, it may be a better choice to explicitly store /boot, /bin, /usr, /etc on the SSD, and store / (ie, all others) on the HDD. You will have to decide how large a partition you will need for each of these directories.

---

### Post by offgridguy on 2012-10-24
Thank you, chilisastry, i have gleaned a lot of info from your post's.

---

### Post by bab1 on 2012-10-24
> **chilisastry said:**
> Bab1 is absolutely correct in his recommendations.  [Thanks, Bab1.  I did not know that /var has volatile data.]

First, depending on your RAID controller, it is best to have identical disks in your RAID array.

Second, HDD (Hard Disk Drive) and SSD (Solid State Drive) have significantly different characteristics.  HDDs can tolerate far more write cycles than SSDs; with excessive writing and re-writing on the same region of an SSD, that region will start to develop failures ('bad sectors').  SSDs do not have any mechanical movements internal to them, so there is no 'seek' time, and speeds of silicon chips can be much faster than even a 7200 RPM hard drive.  So, intrinsically, SSDs are much faster, both for writing and for reading of data, than HDDs, but tend to develop failures if written to too often.  ['Too often' is a very loose term; actually SSDs can handle hundreds of thousands or millions of write cycles over their lifetime, but HDDs can probably handle billions or trillions of write cycles in their lifetime.]

Because of these characteristics of SSDs, it is best to use them to store data which will not change very frequently, and which must be read very fast.

Bab1 recommends - correctly - storing the operating system files and applications files on the SSD (the / node of the file system) AND storing the files that change frequently on a HDD (swap, /home and /var; /tmp is another such candidate).  Alternately, it may be a better choice to explicitly store /boot, /bin, /usr, /etc on the SSD, and store / (ie, all others) on the HDD. You will have to decide how large a partition you will need for each of these directories.

Yes indeed, I forgot about /tmp.  The /var branch holds the log files and the all files if you run an apache web server. There are so many factors that need to be taken into account.  The sad thing is the SSD will never hold anywhere near its capacity as you really don't need more than 20GB for all of the OS.  If the OP can return it for a much smaller one (60 to80 GB) he will save some money.

In a machine that is not heavily loaded the advantages of RAID (high availability) are NOT outweighed by the downside lack of recoverability when using disks larger than 1TB.

To summarize my thoughts here; return the SSD for a smaller one.  The when installing you can decide on what partitions (swap, /tmp,  /home and /var) to create on the HDD.

---

### Post by Wim Sturkenboom on 2012-10-24
I suggest that you keep the partitioning scheme simple. Creating partitions for nearly every 'subdirectory' under '/' (the root partition) has the big disadvantage that you need to predict how large they are going to be. Make e.g. /var or /usr too small and you run into problems (while you still have space elsewhere). For normal 'desktop' use, partitions for '/', swap and '/home' should be sufficient.

For servers, an other approach can be chosen.

---

### Post by oldfred on 2012-10-24
Are you also going to install Windows? 

A 256GB SSD is huge as a boot drive. I have a 60GB SSD with both Precise & Quantal in 28GB / partitions. I configure my system partition to include /home but have swap & all data on my rotating drives. My /home is really only the hidden user configuration files. Even some hidden data folders like  the Firefox & Thunderbird profiles are on my rotating drive.

If system is new, you may have UEFI. Both Windows & Ubuntu can be install in either BIOS or UEFI but both must be the same. Normally how you boot installer either UEFI or BIOS is then how it installs.

If you have UEFI you have to use gpt. Windows will only install in UEFI mode if drive is gpt. But if you are only installing Ubuntu I also suggest gpt as the newer partitioning scheme over MBR(msdos) as then you do not have to worry about primary, extended or logical partitions as in effect they all are primary. 

I use gpt on SSD, have MBR on one drive and gpt on another rotating drive.

Lots of technical details on Linux on SSD.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Since your rotating drive is 1TB, read this. 
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
I now have my main installs on my newer SSD, but keep working installs of Ubuntu(not Knoppix) on every hard drive. But I do have Knoppix on a flash drive as an ISO I can directly boot.

---

### Post by geomcd1949 on 2012-10-25
This amount of information is way too much for me to digest in the time before I start to assemble the computer. My plan is to install the SSD by itself, then read and re-read the posts kindly posted here until reasonably confident enough to add the HDD and do a complete Ubuntu re-install. Deep thanks to all for great advice.

---

### Post by chilisastry on 2012-10-26
You are better off installing with the HDD, and then start using the SSD after you are familiar and confident about the process and issues.

Two important, practical tips about the /boot partition.

First, many of the older BIOS programs do not recognize cylinders on a disk above a certain number (I don't remember the limit, but it is in the hundreds).  So make sure the /boot partition starts on a cylinder below this limit; making the /boot partion the first on on the disk will guarantee you that.

Second, grub (the loader used by Linux) does not seem to find a partition numbered above 8 (such as /sda9).  So make sure the /boot partition is numbered in the range /sda1-/sda8 (or /sdb1-8 or /sdc1-8, etc as the case may be).  You will be able to see the partition number while creating partitions during the Linux installation.  Note that partitions on a disk are numbered in the order they are created (within the restriction that logical partitions are numbered from 5 up), so it is very possible that /boot can be numbered /sda9 even if it is placed at the beginning of the disk (ie, low cylinder numbers).

---

### Post by Wim Sturkenboom on 2012-10-28
> 
First, many of the older BIOS programs do not recognize cylinders on a disk above a certain number (I don't remember the limit, but it is in the hundreds). So make sure the /boot partition starts on a cylinder below this limit; making the /boot partion the first on on the disk will guarantee you that.

I think that that will be so old that the hardware will not be even capable of running the latest versions of Ubuntu.

---

