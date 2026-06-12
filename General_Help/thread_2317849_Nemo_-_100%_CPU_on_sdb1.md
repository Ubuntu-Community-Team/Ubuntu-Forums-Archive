---
title: "Nemo - 100% CPU on sdb1"
date: 2016-03-20
forum: General Help
---

### Post by futz2 on 2016-03-20
Just recently I noticed that whenever I'm on sdb1 in Nemo the machine slows to a crawl. I looked in System Monitor and CPU usage is 100% on one core while I look at sdb1. No other partition does this - I can look at sdb2, sdb3, sdb4, sdc1, sdc2, sdc3, sdd1, sde1, sde2, sde3, sde4 and so on. All show CPU cores basically idling while looking at them, but when I click on sdb1 it goes crazy.

First I moved all files off sdb1 (and sdb2 just in case) and deleted the sdb1 partition. Made a new partition and formatted ext4. Tried again and it's the same - CPU 100%. Weird.

So I changed out the drive. New 3TB drive split into four sdb primary partitions. Same thing - sdb1 makes CPU usage go crazy and the machine bogs down. Other partitions are fine.

I can look at sdb1 with Nautilus and CPU usage is normal near-idle. But Nautilus has been ruined - it's nearly unuseable. I need Nemo, but it appears it may have a bad bug. Any ideas?

BTW: I always have all previews disabled in Nemo, so that's not it.

Here's a screen cap of the problem. The first half where the CPU cores are idle I'm looking at sdb2. The second half is when I look at sdb1. There are no files on sdb1 at present - it's a new drive. Pretty weird, huh?
[IMG]http://i.imgur.com/U96F4kj.jpg[/IMG]

---

### Post by DrDexter on 2017-01-24
Hi Futz2,
same issue here but I've solved it deleting an old bookmark in nemo which was pointing to a folder (it no longer exists) inside the partition which generate the cpu peak usage.
I know this is an old thread but I hope this can help you or anyone still experiencing the same problem.

---

### Post by futz2 on 2017-03-30
> **DrDexter said:**
> Hi Futz2,
same issue here but I've solved it deleting an old bookmark in nemo which was pointing to a folder (it no longer exists) inside the partition which generate the cpu peak usage.
I know this is an old thread but I hope this can help you or anyone still experiencing the same problem.
Hey thanks DrDexter! That was exactly the problem. The strangeness is cured. I didn't even know that bookmarks existed. Must have set the two I had on sdb1 by accident.

---

