---
title: "Resizing partitions with gparted - will it erase my files?"
date: 2007-09-15
forum: General Help
---

### Post by AstarothCY on 2007-09-15
I have the following setup:

ubuntu root - 50GB
ubuntu home - 413GB
linux swap - 2GB

Obviously my root partition is too big (I wasn't sure what actually goes in there when I was installing) so I want to shrink it and enlarge the home partition. Can I do this without losing or risking losing any data? Both partitions are ext3.

---

### Post by forestpixie on 2007-09-15
I could be wrong - but I believe that it will want to add any gained space to the beginning of the partition rather than the end - I'm assuming your partitions run in root, home,swap order, and I'm sure you can't move partitions.

There's nothing to stop you shrinking the root partition and creating a new partition in the empty space. You just need to then look into mounting the new one.

If I'm wrong someone will say so I expect :)

I'd be inclined to make sure you've got backups before you start working on partitions though.

---

### Post by Sef on 2007-09-15
> Can I do this without losing or risking losing any data?

**Back up** your data.  Resizing a partition always involves risk.

---

### Post by Slim Backwater on 2007-09-15
> **AstarothCY said:**
> ... I want to shrink it and enlarge the home partition. Can I do this without losing or risking losing any data? Both partitions are ext3.

First, assume that it will erase everything and take the appropriate steps (backup, prepare to restore) then try it.

In my opinion, I don't like the plan though and would suggest you leave it.  The MFT has 4 "slots" (primary partitions) and generally they are in order so the first partition defines an area at the start of the disk, the second is after the first and the third is after the second.

If you shrink the first partition, you will have a gap between the first partition and the second partition, which you could then define with the 4th slot.  This would be valid, but dirty.  

Here's another way to explain it: sda1 (the first primary partition) would be your reduced root, sda2 (second primary partition) would be your home, sda3 (third primary partition) would be your swap and sda4 (final primary partition) would be the space between sda1 and sda2.

You might reduce your root partitoin and move your second partition up, but it would still be the third primary partion and the entire 430GB has to be moved, that's alot of data and will take hours.  

50 GB for root isn't too bad anyway, all your system software is installed in /usr which will only grow, and your root also holds /tmp which can be any size at any time and stuff breaks if /tmp fills.  If you shrink root as much as possible, then plan to create partitions for /usr and /tmp.

In the end, it's a little big (I usual make 10 or 20GB / partitions, but then I also use LVM2 for the remainder so I can create partitions on the fly to handle /usr /tmp, etc as the need arises) but you'll waste alot of time and make alot of trouble for yourself if you go ahead with the resize.

wow, that was alot longer than I expected.

HTH, HAND.

---

### Post by AstarothCY on 2007-09-16
Thanks for that, Slim. Also, you've convinced me Sef, I will buy a 500GB drive and just do things the simple, rational way.

---

