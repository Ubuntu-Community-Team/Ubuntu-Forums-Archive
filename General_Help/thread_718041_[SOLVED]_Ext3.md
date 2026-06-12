---
title: "[SOLVED] Ext3"
date: 2008-03-07
forum: General Help
---

### Post by itix on 2008-03-07
How do you format something in ext3 without giving 5% to root with Gparted (or any other application for that matter)?
I searched with google and on this forum and the linuxforum but couldn't find anything but bug reports and meaningless information.

---

### Post by PinkFloyd102489 on 2008-03-07
I dont think it's possible. You can switch to something like ReiserFS, which I prefer over ext3 anyway.

---

### Post by uberlube on 2008-03-07
:confused: what do you mean by 5% to gparted and what are you trying to format?

---

### Post by PinkFloyd102489 on 2008-03-07
Im not entirely sure why it reserves 5% but I think it's for Ext3's journal.

---

### Post by itix on 2008-03-07
I am trying to format an external harddrive. In fact, I have already fomatted it but it consumes 5% of the disk.

This is a post from another thread I made a couple of hours ago:
[http://ubuntuforums.org/showpost.php?p=4471522&postcount=14](http://ubuntuforums.org/showpost.php?p=4471522&postcount=14)

---

### Post by uberlube on 2008-03-07
Ah I see. I formatted my 250 gig external drive to ext3 and I never noticed that and I used parted magic to do it. Im gonna go check and see if that happened to me as well.

---

### Post by bodhi.zazen on 2008-03-07
with tune2fs:

```
sudo tune2fs -r 0 /dev/xxx
```

where /dev/xxx is the partition.

This reduces the reserved blocks which is different from the size of the journal.

[http://www.netadmintools.com/html/tune2fs.man.html](http://www.netadmintools.com/html/tune2fs.man.html)

---

### Post by kebes on 2008-03-07
> **itix said:**
> How do you format something in ext3 without giving 5% to root

The ext2 and ext3 filesystems reserve 5% of disk space for the root user by default. This is done so that a full disk won't prevent the operating system from running (and doing regular things like make log files), and also to prevent file fragmentation. If you actually fill your disk past that 5% buffer you will suffer some performance loss due to fragmentation.

If you really want to get rid of the 5% reserve, you can use the command "[tune2fs]("http://www.linuxcommand.org/man_pages/tune2fs8.html")", which is installed by default. (See also [this post]("http://www.linuxquestions.org/questions/linux-hardware-18/3gb-of-disk-space-lost-disk-space-problem-or-mother-board-conflicts-with-hdd-262802/").)

---

### Post by itix on 2008-03-07
Thanx to everyone :)
Problem solved...

---

