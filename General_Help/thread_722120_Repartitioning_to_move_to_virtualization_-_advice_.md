---
title: "Repartitioning to move to virtualization - advice requested."
date: 2008-03-12
forum: General Help
---

### Post by kaens on 2008-03-12
So I have a laptop that's currently dual-booting windows XP and Ubuntu, and I'm looking to get rid of the XP partition, as I don't use it for much and just run ubuntu on the system. There is also a vendor-placed "recovery" partition, which I don't need.

Ubuntu is in the middle of the drive.

Is it safe to remove the partitions on either side of the Ubuntu install and extend the (ext3) partition either way to take up the entire drive, or should I dump my /home/ directory and list of installed packages and reinstall fresh?

---

### Post by forestpixie on 2008-03-12
you'd need to delete the partitions either side - but to use space to the left (beginning of drive) you'd have to move the ext3 partitions before you coudl do any resizing

there's 3 alternatives - do that, use the space as storage - then just reformat the partitions, or reinstall 

I personally would just make another partition from the ntfs ones - delete the xp and recovery and make 1 ext3 

assuming that the 2 ntfs drives are at the beginning

sudo fdisk -l

would answer that

---

### Post by undecidable on 2008-03-12
The old versions of gparted and qtparted (a few months ago)
would not extend a partition left,
so if you created free space to the left of a partition
you could not extend it to that space,
and would have to put a new partition in that space.

I am not sure if the latest versions remove this limitation. 

If not,
you could create a new partion on the left of the Ub partition
and move /home there.
Your Ub partition you could extend to the right.

---

### Post by dcstar on 2008-03-12
> **kaens said:**
> So I have a laptop that's currently dual-booting windows XP and Ubuntu, and I'm looking to get rid of the XP partition, as I don't use it for much and just run ubuntu on the system. There is also a vendor-placed "recovery" partition, which I don't need.

Ubuntu is in the middle of the drive.

Is it safe to remove the partitions on either side of the Ubuntu install and extend the (ext3) partition either way to take up the entire drive, or should I dump my /home/ directory and list of installed packages and reinstall fresh?

Make a separate partition for the VMs - a high performance filesystem like Reiserfs will give better performance.

Be careful if you remove your boot partition - Grub may be removed with it.......

---

### Post by justleen on 2008-03-12
I'd leave the ext3 partition where it is, and use the old windows partition as extra space. 

Its kind of tricky to move the whole partiton to the beginning of the disk, and there is no need to. Its doent really matter where what resides..

I would create a SuperGrub disk though, like dcstar mentions, Grub may be at risk.. better be prepared then sorry

---

