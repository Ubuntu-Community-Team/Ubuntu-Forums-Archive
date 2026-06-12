---
title: "Newb question about NTFS with Ubuntu"
date: 2007-01-26
forum: General Help
---

### Post by Paqman on 2007-01-26
Hello folks,

I'm tinkering with the idea of installing Ubuntu dual boot on my Win XP machine.

I've had a quick search but can't seem to find an answer to my question:

I use a seperate drive for my data than my applications. Obviously the data drive was formatted NTFS by Windows. Would this be a problem for Ubuntu?

So:
C:/ NTFS with WinXP (and potentially Ubuntu)
D:/ NTFS with all my data

---

### Post by housam on 2007-01-26
No , there is no effect that ubuntu can do to your data files / directory.
You need to resise one of your partitions ( C  or D )to create two new partritions for ubuntu with different  format style ( ext3 for the root partition and swap for the swap partition ) 
Also you can access the ntfs partitions from ubuntu .

---

### Post by taurus on 2007-01-26
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Paqman on 2007-01-26
But will Ubuntu be able to write to the NTFS data drive? That's all my data, i'd need to be able to use it. Would I have to convert it to FAT32?

---

### Post by housam on 2007-01-26
No you don't have to convert it. read the links given by taurus about partition mounting and you'll get every thing fine.

---

### Post by taurus on 2007-01-26
Write to ext2/ext3 from Windows.
[http://www.fs-driver.org](http://www.fs-driver.org)

Write to ntfs from Ubuntu.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Paqman on 2007-01-26
> **housam said:**
> read the links given by taurus about partition mounting 

Yeah, my eyes kind of glazed over when I looked at that one. Since I have no idea what it's talking about, i'm reluctant to fiddle about with that.

Is it basically saying that you can give Ubuntu permission to write to an NTFS disk? I think what i'm wanting to do here might be a little beyond my expertise...


EDIT: I'd be running Ubuntu in 64-bit on an AMD, if that makes a difference?

---

### Post by housam on 2007-01-27
It w'll be a little more faster than 32bit.

---

### Post by Goober on 2007-01-27
If you are looking for a fairly-userfriendly method of partitioning your system to install Ubuntu (and formatting the required ext3 for Ubuntu, and the swap, then the Gnome Partition Editor LiveCD should be of service:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

I assume that you know what a LiveCD is, and how to burn that .iso to make the proper image.  If not, we can explain it.  

Your Ubuntu Partition should be larger then 5 gigs, mine is 40 gigs, and your swap is supposed to be small, mine is 1 gig.

---

### Post by Paqman on 2007-01-27
Cheers!

Yep, i'm ok with burning disk images, etc. I'm fairly good with computers generally, but Linux has always seemed to be just that bit beyond an intermediate user's comfort zone. One of the things I like about Ubuntu is how user friendly it seems.

Open source will only make real headway in the OS wars when a novice can put the disk in and have a working OS by following simple screen prompts.

---

### Post by Paqman on 2007-01-31
Ok, having read up a bit more i've decided on a plan. Since the whole point of having two drives is to physically seperate OS/aps and data I was thinking:

Drive 1:
NTFS partition (Win XP + aps)
EXT3 partition (Ubuntu root)
Swap partition

Drive 2:
NTFS partition (shared data, mounted)
EXT3 partition (Ubuntu home)

Does this seem practical/logical? And what sizes are sensible for the root and home partitions?

---

### Post by Cobikegeek on 2007-01-31
That partitioning scheme should be fine.  Don't forget to defrag your ntfs partitions before doing any resizing and back up just to be safe.

Your linux root partition only needs to be 10 to 20 gb and /home needs to be big enough for all your data files.  Linux doesn't use drive C: or D: designations, so your partitions will be listed like files /dev/sda1 /dev/sdb1  /dev/hda1  depending on what type of drive (sata, ide...)

During an Ubuntu install Gparted is the partition manager.  Be sure to select the option to manually partition and resize your ntfs partitions.  When you create the ext3 and swap partitions use the drop down box to select mountpoints: "/" for root, "/home" for home and "swap"  (you'll see how it works).  Get everything set up the way you want it and select Apply (nothing changes until then).  When asked if you want grub installed in the MBR say yes.  That allows you to choose your OS during start up.  

I suggest reading the psychocats links about dual booting and partitioning that Taurus referenced in an earlier post before you do anything.  

Also, about your comment that open source needs to be easy to install--it is if you are just doing a simple install where ubuntu is the only OS on you machine.  Dual booting and using 2 hard drives complicates the process somewhat since you must resize and create new partitions.  Good luck.

---

### Post by Paqman on 2007-02-02
Well, i've got Ubuntu installed and running happily, but I can't for the life of me get the write permission for the NTFS partition.

I had it mounted, but no write permission and I can't seem to get ntfs-3g installed and running (or ntfs-config) Trouble is i've tried to follow about 15 different how-to guides and I think i've got it all messed up now. 

The partition is currently unreadable. I'm using Dapper on an AMD64, any help anyone could sling my way would be much appreciated.

---

### Post by feest on 2007-02-02
by default ubuntu can read ntfs partitions, however it cannot write. using some beta software this shloulb be possible but i don't know exactly wich...

---

### Post by Paqman on 2007-02-03
I believe its ntfs-3g, but I can't get that installed and running for x64

---

