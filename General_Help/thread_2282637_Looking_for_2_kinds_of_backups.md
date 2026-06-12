---
title: "Looking for 2 kinds of backups"
date: 2015-06-15
forum: General Help
---

### Post by ross4 on 2015-06-15
I am running a dual-boot XP and Ubuntu 14.04.2 LTS on a single hard drive laptop (see below).
I would like to do two kinds of backups on my system. First, the basic type of backups where I can retrieve lost files or directories etc. It looks as though deja-dup should be ok for this but would appreciate any comments.
Second, I want to play around with installing/messing around with a few programs and linux projects and I would like to be able to restore my Xubuntu to exactly the way it was before I started to do this messing around. I'm fairly confident that this messing around will not affect the XP partition but perhaps the option to restore my entire drive would be prudent. I have several USB hard drives that I can use for back-up.

   My system:
Toshiba Satellite  
 P100
 Intel core two CPU
 T5500 @ sign 1.66 GHz
 1.67 GHz, 2.00 GB of RAM

---

### Post by papibe on 2015-06-15
Hi ross4.

For personal files there are lots of options. I think deja-dup would be just fine. I'd recommend doing the exercise of testing your backups by recovering some files from them.

For the system itself, you require an special tool as you can't create a perfect copy of a partition while it's mounted. You would need to use a live CD/USB. The simplest option I can think is to use the Ubuntu installation media, and select 'Try Ubuntu' instead of installing. When you get to the desktop you can use 'Gparted' to copy your root partition to an external drive.

This works better if you have your /home on a separate partition. This way you would be copying/cloning a smaller root partition.

Does that help? Let us know if you need more help with that.

Regards.

---

### Post by monkeybrain20122 on 2015-06-15
To clone your / system (as papibe said if you have a separate /home you can keep root very small) use fsarchiver. It is in the repo
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

More details, see [http://ubuntuforums.org/showthread.php?t=2221842](http://ubuntuforums.org/showthread.php?t=2221842)

Also, you should either get rid of XP or at least cut it off the internet.

---

### Post by JKyleOKC on 2015-06-15
> **ross4 said:**
> I have several USB hard drives that I can use for back-up.
Just be aware that backing up a full partition via USB is a slow process, even with USB 3.0 (and many of us still use only USB 2, with a maximum transfer rate around 54 MB/second). The last time I tried it, the process required several DAYS uninterrupted run time to copy a dozen virtual machines, each having 20-GB virtual disk drives or larger. Your Ubuntu partition may be much smaller, but it will definitely take much longer than you expect!

---

### Post by RobGoss on 2015-06-16
Hello and welcome, I would recommend using Clonezilla for a complete backup it will create an ISO of your entire system and if you need to restore it, it will restore it back just the way you had it flawlessly. [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Bucky Ball on 2015-06-16
I use Luckybackup for files and directories (install it from the repositories) and Clonezilla for partitions and disks. That's it. I do the former about twice a week (occasionally more often) and am trying to get into the routine of partitions once a week and the whole disk once a month. :)

Here's a bunch of Clonzilla links:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by monkeybrain20122 on 2015-06-16
I know a lot of people use Clonzilla but it is less flexible than fsarchiver and more complicated to use. If you plan to resize partitions (or in general do anything with them) don't use clonzilla.

e.g With fsarchiver you can restore to partitions of any size as long as it is big enough to hold the content. With Clonezilla you cannot restore to a smaller partition even if the original is mostly empty. So you would have to do something slow and potentially risky like using gparted to shrink the original partition first.

fsarchiver uses only one command to clone and one to restore and it permits live imaging, that is, you can use your computer even when you are cloning and it is very fast.

---

### Post by ross4 on 2015-06-17
Hi, 
 Thanks for these suggestions. I am now actively reviewing what I can find out about Clonzilla and fsarchiver.   My backup sizes are really quite minimal and so is my daily 'production'. Quite a while ago, I moved all pictures, videos and music onto USB hard-drives and on a regular basis I copy my home directory to both of the drives. 

 What I am looking for is an easy way to get back to a configuration (all added/removed programs, settings, templates, etc. as they were) that was working well at some point. 

 The more I think about it, though, is that what I really need is to get a better working knowledge of Linux in general so that I can do things at a deeper level and be able to follow various postings on how to (un)do things. 
 Recently, I had to re-install Xubuntu and, although I gone through the whole process of partitioning & resizing partitions previously with great success, I could not figure out at all what was going on when I tried to re-install. 
 I could not map things that I saw on parted and other source of information about the partitions onto the choices I saw on the installation menu. After re-installation, I ended up having to move /home to another partition (thanks to some excellent instructions on how to do this!).
 

 I should probably get hold of another machine, too, in order to experiment!
 

 Regards

 Ross

---

### Post by Bucky Ball on 2015-06-17
You could play around on a virtual machine if you have the RAM and specs to handle it. That way, break away! You can also install to another partition. You have a stable install for your day-to-day computing and another for your breakage pleasure. I have four spare partitions for experimenting and also used to run virtual machines quite a bit in 12.04 LTS (VMs are great fun, you can try all the distros you've been curious about but may never bother installing). I haven't diddled with either on 14.04, though, due to not having the diddling time nor the time to fix things if something does go seriously wrong. :)

---

