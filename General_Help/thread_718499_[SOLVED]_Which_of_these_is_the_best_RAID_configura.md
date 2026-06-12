---
title: "[SOLVED] Which of these is the best RAID configuration?"
date: 2008-03-08
forum: General Help
---

### Post by Monk-e on 2008-03-08
Hey,

I've got some money to spend and I'm going to implement a software RAID array with lvm over mdadm.
I only have 2 SATA slots in my PC so I'm going for a partial RAID1 (for OS + important data) and a partial RAID0 (for non-critical data) configuration.

I've created 4 possible schemes of what I want to do and put them in an ODG file.
Here's the attachment: [ATTACH]61966[/ATTACH]

It basically boils down to this:
-RAID1: one big volume or multiple smaller volumes?
-RAID0: same question.

Advice would be appreciated, thanks in advance.

P.S. Not sure if this is off-topic in this forum. :)

---

### Post by Toet on 2008-03-08
I always go for the 1 raid partition per disk. Having two raid partitions on a disk will decrease speed when both are used. For example if you have two raid partitions per disk on 2 disks you could have:

raid0 over sda1 and sdb1
raid0 over sda2 and sdb2

If you would copy from one raid to the other raid you lose speed on both. If it would be one raid partition the copy would be more efficient I like to think.

Raid0 can achieve very fast speeds, but only usable for copying a lot or large files. The access time is still the same. Reading files and loading programs will be faster. You will need backup though!

Raid1 is nice when you don't have another device to backup to.

LVM over raid has a bug in Ubuntu you should be aware of that. The readahead settings are not very good. You can bypass that using blockdev setra (in a startup script preferably). Have a look at these links:

[https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/129488](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/129488)

If you are also amazed by this bug (and the time it's filed) Have a vote at:

[http://brainstorm.ubuntu.com/idea/2098/](http://brainstorm.ubuntu.com/idea/2098/)

---

### Post by Monk-e on 2008-03-08
Thanks for your reply.

There probably won't be alot (if any) copying from one of the RAID partitions to the other.
Also, doesn't RAID1 have the same read optimizations as RAID0?

Why is copying from 1 RAID partition to another on the same array slow?

And I'm definitely voting up on that bugfix. :) Thanks.

---

### Post by Toet on 2008-03-08
Copying from 1 raid array to another, where both raid arrays are using 1 or more same disks is slower. This is because they share the same hardware device. For example: you have 3 disks, sda, sdb and sdc and you have two raid arrays, md1 on sda and sdb and md2 on sdb and sdc. 

If you copy from md1 to md2 it wants to read and write to sdb at the same time. The bandwith of sdb if for example 80mb/s, now it will have 40mb/s to read and 40mb/s to write (again for example). Cause the disk is in an raid array it will slow down the whole raid array it's in, both md1 and md2 will perform at 80mb/s (if it's raid0, 2x40mb/s), as fast as 1 disk.

It's just an example, and the figures won't match practice, but it's something to keep in mind.

---

### Post by Toet on 2008-03-08
> There probably won't be alot (if any) copying from one of the RAID partitions to the other.

Then I think it's ok to have more raid partitions on one disk.

> Also, doesn't RAID1 have the same read optimizations as RAID0?

What do you exactly mean by this question?

---

### Post by Monk-e on 2008-03-08
> **Toet said:**
> What do you exactly mean by this question?
What I mean is that RAID0 can read files quicker because you can spread the load over 2 disks and that the same applies to RAID1.

Now back to my original question:
Is it better to have multiple smaller RAID1 or RAID0 partitions inside a LVG or to have one large RAID1 or RAID0 partition inside a LVG?
If you're not sure what I mean please have a look at the attachment in the my original post.

---

### Post by Toet on 2008-03-09
I do not now which read technique mdadm uses for raid1, so you should test if it is fast.

I would go for 1 big raid device and use LVM on that. I see no advantages on the multiple raid array thing.

---

### Post by Monk-e on 2008-03-09
Alright Toet thanks for your time. I'm just going to mark this as solved. :)

---

