---
title: "Partitioning Advice Needed"
date: 2006-12-15
forum: General Help
---

### Post by BarfBag on 2006-12-15
Here's the plan.  My Kubuntu partitions are 20 GB altogether (swap and root).  Windows XP is occupying close to 140 GB of the drive.  This is the way my partitions have been for 3+ years.  I've long outgrown the small 20 GB of space that Kubuntu owns, so all of my data is on the Windows partition.  I want to shrink Windows down to 35 GB (little bigger then Kubuntu, but I've always had trouble installing programs onto separate hard drives/partitions, it probably wouldn't even work in this case because of the file system difference).  Then, I want to create a 110 GB partition occupying the rest of the space for my files.

I surfed around, and so far haven't come across a free partition editor that beats GParted.  Will that nondestructively resize the Windows partition (which is formatted in NTFS)?

Also, what file system do you recommend I make the data partition?  I (obviously) need something that both operating systems can recognize.  A few months ago, I stumbled across a website with a driver that added ex2 support to XP.  Is that still around?  How well does it work?  Is ex2/whatever you recommend a safe file system to use?

Thanks.

---

### Post by meng on 2006-12-15
I would recommend ext3 for your data, and install fs-driver on WinXP.

---

### Post by BarfBag on 2006-12-15
> **meng said:**
> I would recommend ext3 for your data, and install fs-driver on WinXP.

Thanks for the reply.  Can you give me the link to the driver?  I can't seem to find it.

---

### Post by housam on 2006-12-15
Defrag the xp partition first and locate where is the position of the unmovable files. It is important not to shrink the xp partition behind that mark. if it is at i.e. 30% 0f the disc from the left ,then the minimum will be a little more than 30% x HDD size.
Also it is recommended to format the data storage partition to FAT32. It is accessable from both OS.

---

### Post by meng on 2006-12-15
[www.fs-driver.org](www.fs-driver.org)

---

