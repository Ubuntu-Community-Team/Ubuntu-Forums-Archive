---
title: "resize /home"
date: 2007-12-03
forum: General Help
---

### Post by evil316 on 2007-12-03
My /home is full.  Maybe I'm not understanding this right.  Tell me where I'm going wrong with this.  I see threads about resizing / and /home and that's all well and good and I can do that but it was my understanding that / was just one big partition and /home as well as /usr and others are all part of the / partition.  If that's the case then why can't you just change the quota for /home since it's not it's own partition?  With gparted it only shows the / partition as well as swap and whatever the other is that I can't think of right now.  So can I simply change the quota for /home?  Were all these partitions set up in the background during install and I just wasn't aware of how the install was allocating partitions?

---

### Post by drs305 on 2007-12-03
When you installed ubuntu a main / and a swap partition were created. Without intervention by you, your home partition would have been created within the main ubuntu partition. If you are running out of space in /home and you didn't specify a separate partition for it, you are running out of space on your ubuntu partition for some reason. You can check disk usage in terminal with :
```

gnome-system-monitor

```
and
```

df -Th

```
Depending on your hard drive(s), you may be able to create a separate /home partition using gparted or find space from another partition. 

Here are a couple of links. The first one has sections (from left menu) on partitioning in general and making or moving to a separate home partition. The second link discusses moving the home partition. You can also search this forum for threads on moving a home partition.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by metalheart on 2007-12-03
You will not have quotas set on your disks, if you have not set them by yourself. If you can't remember installing quota, then it is probably not set.

---

### Post by evil316 on 2007-12-03
So if I am understanding correctly there is a / partition that was created spanning most all of my hard drive except for swap.  Then the /home partition is inside the / partition?  So can I grow the size of /home within root or am I better off shrinking / and making /home seperate?

---

### Post by rsambuca on 2007-12-03
Open a terminal and enter```
sudo fdisk -l
```and also ```
cat /etc/fstab
``` This will let us see how your drive is partitioned.

---

### Post by metalheart on 2007-12-03
Default Ubuntu install gives all space (except for swap and /boot) to root (/) partition and if your home is full, then your whole disk is full, I think.

---

### Post by evil316 on 2007-12-03
I'll paste the needed info into this thread this evening when I get home from work.  The entire disk is not full.  It is an 80 gig drive in a laptop.  There is 60 some gig available.  Where it shows /home is full is when I run the disk analyzer program under accessories and scan the disk(s).

---

### Post by metalheart on 2007-12-03
This 100 means its total in % for all thats underneath!

---

### Post by evil316 on 2007-12-03
OK, I'll paste the info this evening.  I'm afraid I may be giving misleading information.  Best to get you solid info.

---

### Post by rsambuca on 2007-12-03
> **evil316 said:**
> I'll paste the needed info into this thread this evening when I get home from work.  The entire disk is not full.  It is an 80 gig drive in a laptop.  There is 60 some gig available.  Where it shows /home is full is when I run the disk analyzer program under accessories and scan the disk(s).

LOL !!!

Ahhh...  problem solved.  Don't worry about posting those outputs!

---

### Post by evil316 on 2007-12-03
So what does the 100 mean?  total what?  Total space allowed?  I don't understand it.

---

### Post by rsambuca on 2007-12-03
> **evil316 said:**
> So what does the 100 mean?  total what?  Total space allowed?  I don't understand it.

The format of the top line in that program is very silly/confusing/rediculous, etc.  When you run the program on your /home, the top line will always say 100% usage since it is just going by the space used by all of the files* in that folder*.  Of course it is going to say 100%.  I agree  that is one of the stupidest displays I have ever seen.

---

### Post by evil316 on 2007-12-03
OK, so it's not an issue.  No space problem at all.  I'm surprised more people haven't been confused by that.

---

### Post by drs305 on 2007-12-03
I just looked at the disk usage analyzer and understand how you came by your concern. As metalheart stated, the 100% doesn't mean the partition is full. 

Since you are using GUI programs to look at your hard disk usage, try using system monitor. You can access it via System, Admin, System Monitor or via the command line I mentioned in an earlier post.  It will list each drive in the device column  (hda, hdb, hdc etc; sda, sdb, etc). Each partition of the drive is listed in the Directory column.

The graphical right side of the program lists the % of space used. The columns to the left show you the actual numbers. 

 I think you will get a better idea of how much space you have used and have remaining. Disk usage analyzer is visually interesting but system monitor will display more useful information for your purposes.

---

### Post by evil316 on 2007-12-03
Excellent tip, thanks!

---

