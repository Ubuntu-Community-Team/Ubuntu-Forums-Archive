---
title: "Migrate to new hardware (cloning?)"
date: 2018-09-24
forum: General Help
---

### Post by joshi82 on 2018-09-24
Greetings,

I have an old 16.04 server, that runs headless in our server room. It host our monitoring software (check_mk). The hardware (regular HP client computer, nothing fancy) should be replaced by a nuc for several reasons.
With a Windows-Box I would fire up one of those many imaging tools and clone it, adjusting the partition sizes on the fly (no bashing, just my personal experience so far). Here with the Linux box I am not aware of any
automatic/semiautomatic way of doing that.
To make things even trickier, the source box has 3 physical disks. One is not important here, sdc is hosting /var/ and /opt, the rest is on sda.
Data size is alltogether around 100GB, bit of downtime after business hours is also no big deal.

I would appreciate some input from you gurus :)

Thanks
joshi82

---

### Post by TheFu on 2018-09-24
First, make a backup of anything you can't afford to loose.  People unfamiliar with linux, partitioning, LVM and other storage techniques often choose options that wipe data.

Get the new machine.  Unplug the old disks.  Connect them to the new machine using the same sort of connection sata-to-sata.  If UUIDs are used in the fstab, this should be seamless and "just work."

Boot.   The network adaptor names will change, so fix those in the udev rules or force them to be the same as the old names using grub options.  Up to you.

Be happy.

If you've got SW-RAID setup, things might be a little harder.  Your backups will have the settings.  I've moved SW-RAID between different systems 3 times and they "just worked". I've seen a few people here have issues, don't know why.  Same for LVM setups.  I've moved them without problems, but some people in the forums have had issues, don't know why.

Or a better idea would be to use your existing backup and recovery procedures to move everything over.  If those don't work, then you've learned 2 things.  
a) the procedures were never good.
b) fixing the process until they do work should be the goal. After all, having a system running that doesn't have a way to restore is foolish.

It isn't often that we ever restore directly to identical hardware after a fire, right?

There are many other ways to accomplish this - dd, ddrescue, partimage, fsarchiver, aptik and the 50+ backup/restore tools, but since this is your first post, I'm loath to suggest anything new to you.  As long as the storage appears to be where it is supposed to be after boot, it really doesn't matter what happens underneath at the disk, partition, lvm, symbolic linking or with storage pools.

---

### Post by HermanAB on 2018-09-24
Hmm, if the machine is old, then it will likely fail, the moment you bring a screwdriver near it and if you do manage the move the disks, they may not last long after.

So, as said above, first make a backup.

---

### Post by mastablasta on 2018-09-25
> **TheFu said:**
> 
Or a better idea would be to use your existing backup and recovery procedures to move everything over.  If those don't work, then you've learned 2 things.  
a) the procedures were never good.
b) fixing the process until they do work should be the goal. After all, having a system running that doesn't have a way to restore is foolish.


true. and can be cruel if you crippled the data and found out that the process didn't work at the point when you though you were backing it up :)

i sense the OP also want to change the disk drives to new ones. 

i used clonezilla to clone bit-by-bit a failing disk drive to a brand new one. i then stretched the old partitions (new disk was much larger) using windows tools (as it was a windows drive), however this can be done much the same will linux tools like gparted for example.

---

### Post by TheFu on 2018-09-25
Moving to a new disk ....

If moving from disk-to-disk, the same rules apply about sector alignment for all OSes. That doesn't change. "Really old" disks are probably 512b sector sized. Newer disks can be either 512b or 4Kb sector sized. Make certain any partitions begin on a sector boundary.

Resizing partition is possible, but I think doing that alters the UUID.  It has been a few years since I did that. Just something to be aware about. The only place that matters is in the fstab. Fixing that is a common thing whenever storage is changed.

If LVM is used, it would be smart to use backup and restore methods.  In a business, I can't imaging setting up a physical system without using LVM. The added flexibility is so great, I'd hate to be without it.

You can clone at the these different levels:
* file system
* partition
* whole physical drive
Each has pros and cons.

---

