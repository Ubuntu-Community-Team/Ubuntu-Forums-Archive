---
title: "Need help sharing drives on MacBook Pro"
date: 2006-12-08
forum: General Help
---

### Post by commonmanthemes on 2006-12-08
Hey guys-

I've got a MacBook Pro (2.0GHz Core Duo) that is running Tiger and Edgy with rEFIt and Boot Camp.  The thing is, I want all of the music I rip to go on a drive that both Tiger and Edgy can access.

-I tried partitioning before the Mac OS install.  No good because Boot Camp makes you have 1 partition before you use it.

-I also tried taking my 32GB for Linux and cut 15GB out of it for this drive.  But, all I can do is make it free space.  Ubuntu's installer partitioner doesn't support HFS (I need HFS case-sensitive, non-journaled, right?)

-I tried taking this free space back into Tiger, but Disk Utility won't alter anything at this point.

Please help!

---

### Post by siepo on 2006-12-10
Fat32 should work fine; it is what I use (on a non-pro macbook).

If you can't convert free space to a partition, maybe it is because you already have 4 partitions: one  for EFI, one for Tiger, one swap and one for Linux. You are limited to 4 partitions on an Intel Mac, but you can use a swapfile instead of a swap partition, and then you can have your fat32 partition.

---

