---
title: "Help needed with Paritioning"
date: 2007-11-07
forum: General Help
---

### Post by SRitter1117 on 2007-11-07
My current partitions are as follows:

/dev/hda1 - NTFS - /media/hda1  
/dev/hda2 - ext3 - / 20 GiB (ubuntu)
Unallocated - none - 160 GiB
/dev/hda3 - Extended
    /dev/hda5 - Linux-swap - 3.24 GiB

The machine has 2 GiB of RAM, I think 3.24 may be too much for the swap, should I make this smaller?  I read something if you have more than 512 mb of RAM, the swap may not be used.

The main issue though is I want to take the free space and create 3 additional 20 gig ext3 partitions (to test 3 other distros at any given time), and a 100 gig ext3 partition to be shared by all (except vista).

gparted (or qtparted) won't let me make that free space into an extended partition, I think it's because there already is an extended partition?

Can I boot with the live CD and resize /dev/hda3 to include all of the free space and recreate the smaller swap /dev/hda5 and then the 4 additional partitions in it, or do I need to delete everything except the ntfs partition and start over?

---

### Post by SRitter1117 on 2007-11-07
It looks like booting with the live CD and resizing the extended partition worked.

---

