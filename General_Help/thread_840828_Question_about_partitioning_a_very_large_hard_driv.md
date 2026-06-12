---
title: "Question about partitioning a very large hard drive"
date: 2008-06-25
forum: General Help
---

### Post by Alex Deez on 2008-06-25
I just got a 640GB hard drive and I'm wondering if I should just make one partition that takes up the whole disk, or split it in two.  This drive will be used only for data.  I guess I'm wondering if there are disadvantages to having a partition that big.  I'm planning to use ext3 but I'd be willing to use a different filesystem if someone has a good argument for it.  Thanks for your help!

---

### Post by niyonk on 2008-06-25
Partition part of It, you might later change your mind...:)

Anyway, i think partitioning the whole disk into one partition will make reading slower.
Let me suggest 3 partitions. (Docs, Movies/TV&Music, anything else?)
As for the filesystem, ext3 is fine \\:D/, unless you would like to access it from a Windows machine. 
Cheers! :guitar:

---

### Post by VMC on 2008-06-25
> **Alex Deez said:**
> I just got a 640GB hard drive and I'm wondering if I should just make one partition that takes up the whole disk, or split it in two.  This drive will be used only for data.  I guess I'm wondering if there are disadvantages to having a partition that big.  I'm planning to use ext3 but I'd be willing to use a different filesystem if someone has a good argument for it.  Thanks for your help!
Speaking of arguments for file systems. Here's one I ran aceoss and worth the read. I guess it all depends on your wants , uses and needs:
[http://linuxgazette.net/102/piszcz.html](http://linuxgazette.net/102/piszcz.html)

As far as how many, one question is, do you have Windows installed somewhere? If so, NTFS one be one consideration. The other thought is if you want to backup your system, it's good to have one just for that purpose.

---

### Post by Alex Deez on 2008-06-25
I'll check out that article.  Also I back my stuff up to an external drive that's formatted NTFS.  I don't run Windows but sometimes I trade with people who do.

---

### Post by Alex Deez on 2008-06-25
Oh yeah, I will probably end up going with 2 or 3 partitions the more I think about it.  Although I don't think I'll divide my media up according to the partitions.  I have been thinking it's probably better to have that much stuff spread out over a few partitions just in case one develops a problem.

---

### Post by cdtech on 2008-06-25
Always better to have separate partitions on a drive that size. If you have one large partition for everything, if it crashes you loose everything. I split mine into several partitions and mount them accordingly.

---

