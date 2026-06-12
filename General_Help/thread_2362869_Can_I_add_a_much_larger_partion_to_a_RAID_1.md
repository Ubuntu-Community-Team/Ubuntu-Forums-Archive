---
title: "Can I add a much larger partion to a RAID 1?"
date: 2017-06-02
forum: General Help
---

### Post by bobnn on 2017-06-02
So I've outgrown my 1TB drives, with Raid 1 partitions of 900+GB for  / and few GB for swap.

Can I fail and remove the partitions for one disk,  power down, put the new disk in place of the one failed, partition the new one for / with a much larger partition (1.8+ TB) then add that to the / md device and let it mirror?  (and then repeat with the remaining 1 TB device)

Or do I need to use the same size to mirror, then grow the  / partition to use the new space?

I was looking at the process at this link, [https://zackreed.me/increasing-the-size-of-mdadm-raid1-disks/](https://zackreed.me/increasing-the-size-of-mdadm-raid1-disks/)  where he says he mirrored, then grew.  But his partitions 1 on the new disks already looked bigger when he added them.

ETA:  Oops, Ubuntu 14.04, kernel  3.13.0-117-generic #164-Ubuntu SMP

---

### Post by bobnn on 2017-06-05
So I did it and found out.  mdadm  lets you add the larger partition on the new drive to the RAID1 and resync the data to it.  Then replacing the other drive gets it resynced, too.

But the RAID1 device, and therefore the ext3 filesystem are still the same size.

You have to grow the RAID1, then grow the ext filesystem to, which require at least one fsck, maybe more.

And don't forget grub-install on each new disk!  That cost me a couple hours, because I hadn't figured out that I could use the BIOS to load from the disk that still had grub properly installed, and so went into recovey mode with an install disk.  D'OH!

---

