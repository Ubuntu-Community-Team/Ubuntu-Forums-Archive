---
title: "Advice needed: (not) partitioning large harddisk"
date: 2008-04-10
forum: General Help
---

### Post by akudewan on 2008-04-10
I bought a 320GB SATA harddisk yesterday. I want to keep this as one large partition, and I formatted it in ext3.

I use [IFS]("http://www.fs-driver.org/index.html") for accessing my ext3 partitions in windows. Windows, however, hung while I was playing a game, and when I booted into linux after an unsafe reboot, fsck was showing me a hell lot of errors. It was also showing something along the lines of "Buffer IO errors", and prompted for "Force overwrites". Since I had nothing of value on the new harddisk, I simply deleted the partition and re-formatted it.

This incident has scared me a bit. What if something like this happens when I have important data on my drive? Windows will hang, there's not much I can do about that. But can I take any extra precautions to make sure something like this doesn't happen ?

Would it be advisable to partition this disk? (I don't really want to do that)
Should I use another filesystem like Reiserfs or something ?

---

### Post by Trail on 2008-04-10
I am not familiar with the IFS thingy, but is there any option to mount the volume as read-only?

And just a silly though, maybe Windows would be trying to index the ext3 volume and messed up. Maybe disable this. Just a wild guess.

---

### Post by prshah on 2008-04-10
> **akudewan said:**
> 
Would it be advisable to partition this disk? (I don't really want to do that)
Should I use another filesystem like Reiserfs or something ?

> **Trail said:**
> I am not familiar with the IFS thingy, but is there any option to mount the volume as read-only?



Yes, you CAN mount the ext3 partition read-only. If that is not an option, and you NEED read/write access, better to make it NTFS.

---

### Post by akudewan on 2008-04-10
Thanks, I'll use it as read-only in windows. I use windows only rarely, Most of the time I'm on linux.

---

