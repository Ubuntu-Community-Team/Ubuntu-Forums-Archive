---
title: "Problems with 10TB HDD (I/O error,  ext4-fs-error, access beyond end of device etc)"
date: 2020-11-05
forum: General Help
---

### Post by mnxca on 2020-11-05
Hello,

Ive been trying to get a Filecoin Miner setup for the past week on Ubuntu and I started getting some errors that I can't seem to solve.

The errors involve /dev/sda (a brand new WD 10TB HDD).  I started by repartitioning and reformatting the drive.  (the first time I followed some bogus directions that had me format the drive /dev/sda instead of the partition /dev/sda1.

I have already run fsck on the file system, it came back clean.  I tried running a smartctl short test but it would go to 50% and the test would never finish.  I swapped out the SATA cable for another one and it would go to 90% and hang there.  Both SATA cables were from an old motherboard box but were in brand new condition.  It says the test should take 2 minutes, but I left it running several hours.  I moved the drive to a windows machine and ran data lifeguard diagnostic and it passed the short and long tests there.

I'm currently running memtest on the machine to check for memory errors (0 errors so far after 3h 45m).

Anyways, the errors Im getting are as follows:

blk_update_request: I/O error, dev sda sector 217517296 op 0x1:(WRITE) flags 0x0 phys_seg 88 prio class 0
several other errors similar to the above

Buffer I/O error on device sda1, logical block 271895986
(many more errors like the above but with different logical blocks)

EXT4-fs-error  (device sda1):  ext4_wait_block_bitmap:517: comm kworker/u256:0: Cannot read block bitmap - block_group = 8304, block_bitmap = 272


sd 2:0:0:0 [sda] tag#29 access beyond end of device

EXT4-fs (sda1) I/O error while writing superblock
EXT4-fs (sda1) Delayed block allocation failed for inode 270532627
EXT4-fs (sda1): This should not happen !! Data will be lost.

Any ideas are much appreciated here.  The drive itself seems to be ok, so not sure what to do next.

Thanks!

---

### Post by BarnOwl on 2020-11-06
Since it's a new drive, the obvious explanation is that you have a defective drive.  The smart test is a good indicator that there's something wrong with the hardware.

If you have another drive,of any size, to try, you can swap it in to test the cables and connectivity.

I'm not familiar with what kind of formatting you'd need for a Filecoin Minor but, if it's standard partitioning and filesytems, I'd boot from a live Linux that has gparted (I like system recsue CD for this) and redo the partitions starting with replacing the partition table.  

If it's some kind of weird partitioning and/or formatting, you can overwrite the entire drive and start over with:

```
dd if=/dev/zero of=/dev/sd% status=progress
```

Where % is the letter that corresponds to your drive.  That's going to take a while for 10TB.

You can look up badblks and do a destructive test.  For a drive that size it will take days if not weeks.

---

