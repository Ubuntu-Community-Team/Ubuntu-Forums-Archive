---
title: "PS3 - Preformatting with GPartition"
date: 2015-10-30
forum: General Help
---

### Post by bellasnaru on 2015-10-30
hey guys

ok basically, i have a 1TB drive and custom modded it into my ps3 so that i can switch between my ps3 and laptop using a 1TB external drive

But problem is. the ps3 likes to use the entire 1TB

So i was wondering if theres a way that i can use gpartition to make a 500GB Fat32 partition, and then make the rest of the space something the ps3 wont recognize or touch. so that the ps3 will only format and use 500GB

---

### Post by SeijiSensei on 2015-10-30
Sony uses a proprietary partitioning and formatting scheme on the PS3, so I'd bet the answer is no.  I think it takes over the entire drive.  But no harm trying, right?  I would just create two empty partitions with no filesystem at all and let the PS3 decide what to put there.  Let the PS3 do its thing, then remove the drive and examine it from Linux.  If the second partition is still empty and unformatted, format it as you'd like, then put it back into the PS3 and see what happens.

---

