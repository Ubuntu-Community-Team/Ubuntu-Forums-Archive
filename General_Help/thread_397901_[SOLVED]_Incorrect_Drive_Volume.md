---
title: "[SOLVED] Incorrect Drive Volume"
date: 2007-03-31
forum: General Help
---

### Post by htmlland on 2007-03-31
Hi, im quite used to linux by now and I use it regually but im stumped on this one! My hard drive i have just bought is 80GB, i have just mounted it and it is only saying it has 37GB!

I have a screeny here: [http://mf89.com/HDDProblem.png]("http://mf89.com/HDDProblem.png")

Any help would be greatly appriciated!

Mike

---

### Post by pradeepadapa on 2007-03-31
hey man what is ur free space there, nd i think u hav created an 32GB space for /backups.. hw much is the freespace

---

### Post by chewearn on 2007-03-31
On the left side it says 76.69GB, so the drive size is correct.  Your Partition 1 probably does not occupy the whole disk (I noticed the "free space" line after Partition1 in the Partition List).

---

### Post by htmlland on 2007-03-31
Thanks for your reply, it says 39.42GiB (Free Space not avalible). I took a screeny here: [http://mf89.com/HDDFreeSpace.png](http://mf89.com/HDDFreeSpace.png)

Mike

---

### Post by aysiu on 2007-03-31
I've merged your two threads.

By the way, you can attach images here.

---

### Post by chewearn on 2007-04-01
> **htmlland said:**
> Thanks for your reply, it says 39.42GiB (Free Space not avalible). I took a screeny here: [http://mf89.com/HDDFreeSpace.png](http://mf89.com/HDDFreeSpace.png)

Mike

That's probably because the free space in unallocated.
You have two choices:
1. create a partition and format the filesystem.
2. increase the size of partition 1 to 80GB

It has been awhile since I have a Dapper installation, so I can't comment on the Disk Manager apps (why it wouldn't let you create a partition on the unallocated space).  Maybe you can install and use GParted (Gnome Partition Editor).

---

### Post by htmlland on 2007-04-01
cool thanks aysiu i dident know about that and AstalaVista ill have a try installing GParted and ill report back :D

Mike

---

### Post by htmlland on 2007-04-01
I couldent find the software you said but i found one called QTParted whcih did the same thing and it worked!! Im very thankful for you help :).

Thanks Again
Mike

---

