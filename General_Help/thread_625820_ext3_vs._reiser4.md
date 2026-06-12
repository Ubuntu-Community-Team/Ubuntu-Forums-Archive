---
title: "ext3 vs. reiser4"
date: 2007-11-28
forum: General Help
---

### Post by TorchlightJay on 2007-11-28
Hey, I was wondering, for Ubuntu Gutsy (or any Ubuntu or Linux) in general, what's better as far as filesystems are concerned? Reiser4 or ext3 or maybe some other one? I used to use reiserfs then i converted to ext3 which is what I usually use now. I am setting up a new HDD and noticed Reiser4 and I want to use the best that I can. Any advice will work, thanks.

---

### Post by dabl on 2007-11-28
There's really not a clear "better" file system -- if there was, there wouldn't need to be choices!  :)

Here are some links to material that should help you understand the pros and cons:

[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

[http://linux.wordpress.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/](http://linux.wordpress.com/2006/09/27/suse-102-ditching-reiserfs-as-it-default-fs/)

[http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)


I personally have been running XFS filesystems on my desktop for about 2 months now with no problems.  I have observed one odd side effect -- VMWare Player takes FOREVER to close -- like more than 5 minutes after I choose "Shutdown" in the Win XP machine that runs on it.  That's the only issue I've noticed.  I previously ran reiserfs for about a year with no problems, but it does boot slower so I wouldn't use it on a laptop that gets booted often.   Ext3 is fine, except every 30th (or whatever it you set it to) boot is does a lengthy fsck process.   :)

---

### Post by disturbedite on 2007-11-28
ext4 is still under development and its still marked developmental as far as the kernel is concerned.  so if you're a gambling man you could try ext4, but i'd just stick with ext3.

---

### Post by Chuckels550 on 2007-11-28
As always it depends on what you want to do.  Ext3 is native to Ubuntu and is a well supported and robust file system.  I would use it unless there is some other requirement that demands something one of the other file systems provides.  For example, I use Ext3 for the system partition on my MythTV box because it is native to Ubuntu and XFS for managing my video files because XFS is one of the best for deleting very large files like video files.

---

### Post by TorchlightJay on 2007-11-28
Cool, so what filesystems work with Ubuntu? I know Ext3 but what about reiser4 or XFS. I am certain that they interact and what not, I am just curious about installation. SO what is XFS best for, what is reiser best for, what is ext3 best for? I am sure they all ahve benefits over each other, or at least I'd like to think.

---

### Post by isecore on 2007-11-28
If you don't know why you need a different filesystem, then the simple truth is that Ext-3 will do just fine for you.

Asking which filesystem is the "best" for Linux is a strange question since all FS's have different merits and disadvantages. Ext-3 is a nice allround-system that'll work just fine for everyone. 

Like I said, if you don't know why you need anything else, then you don't need anything else. Reiser, JFS, XFS, etc etc are all good and sound filesystems - but you need to choose the FS to suit what you're going to be doing.

---

### Post by Cr0n_J0b on 2007-11-28
for me reiser was faster.

---

### Post by disturbedite on 2007-11-28
Chuckels550 is right, it all depends on what you need/want in your filesystem.  ubuntu supports any FS the linux kernel does, for obvious reasons.

---

### Post by TorchlightJay on 2007-11-29
Cool, I am just curious. I was formating a drive and saw all the other FS listings and was curious as to what the major differences were.

---

### Post by sirdilznik on 2007-11-29
I love reiser4 and have used it in the past with great success.  I still have a left over partition from an earlier install with it and thus use it today also.  However I would not build any new partitions with that file system because its future is uncertain (it doesn't look good).  Between Hans Reiser's legal problems, the kernel devs refusal to include it in the mainline kernel (even though some of the very same features that kept reiser4 from being added to mainline are now part of ext4 which is in mainline...), and the maintainers being down to just a few individuals, it really does seem like reiser4 is going to go the way of the dinoaur.  It's really too bad because it is a superb filesystem that presents many advancements, but it seems like politics are going to kill it.  I hope it survives and somehow miraculously makes it into mainline someday, but that seems doubtful at best.

---

### Post by fjgaude on 2007-11-29
Anyone know when ext4 will be with a Ubuntu release? and when Gparted will handle it?

---

### Post by -grubby on 2007-11-29
> **fjgaude said:**
> Anyone know when ext4 will be with a Ubuntu release? and when Gparted will handle it?

probably not for at least another year or so

---

### Post by bodhi.zazen on 2007-11-29
Well, I have played with all of them and to be honest I did not see any significant performance enhancement between the various file systems for day-to-day usage.

I made my decision based on stability and reliability. IMO, at the time of my review, which was some time ago, Ext3 was the most reliable. Take a look at the vulnerabilities of the filesystems, not just he benchmarks or advantages. What happens in the event of a power failure for example. Or what tools are available for data recovery ?

So read about the file systems and if you like give them a try.

+1 Chuckels550

---

### Post by atlfalcons866 on 2007-11-29
jfs is very prone to fragmentation.

---

