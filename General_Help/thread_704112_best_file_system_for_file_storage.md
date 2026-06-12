---
title: "best file system for file storage"
date: 2008-02-22
forum: General Help
---

### Post by onesojourner on 2008-02-22
I am going to reformat my storage partition. What fiel system should I go with? the partition will be about 400 gigs and I read and write from it a lot. currentlty I am using ext3. Is this the best thing for this kind of storage. I need something that will not freak out if it gets a small error.

---

### Post by yabbadabbadont on 2008-02-22
I would just stick with ext3.

Off-topic: I don't know about you, but I sure am glad that the ice storm predictions were wrong.

---

### Post by onesojourner on 2008-02-22
Tell me about it. It never snows here any more all we get is ice storm after ice storm.

---

### Post by Flyingjester on 2008-02-22
> **yabbadabbadont said:**
> I would just stick with ext3.

Off-topic: I don't know about you, but I sure am glad that the ice storm predictions were wrong.

+1 on sticking with ext3

---

### Post by ryanhaigh on 2008-02-22
I used reiserfs for a while on my 1.5TB system but the slow mounts at startup were a pain and there was no percievable benifit. 

I tried XFS as it is supposed to be good for large files however apparently the risk of data loss is increased for blackout type situation and while I have a UPS it doesn't auto shutdown my system. 

So on my Gutsy install I reformatted all partitions (a LOT of data transfer that day) to ext3 and I think it is actually faster, it was suggested to me that this is because the system is faster when transfering between identically formated partitions rather than 'converting' to a different fs for each device. The fact that 'everyone' uses it also means you might have more luck should you need support, tune2fs anyone.Whats more on the odd occasion that I get around to booting into windows to play some games I can access my files using the fs-driver.org ext driver for windows. btrfs might change my mind but for now I too recommend ext3

---

