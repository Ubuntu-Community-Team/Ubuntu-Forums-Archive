---
title: "Help - I cannot read RAID1 member w/ext4 FS on it"
date: 2012-12-27
forum: General Help
---

### Post by raygeeknyc on 2012-12-27
HI
  I have a remotely located machine running ubuntu 11, on which I've used mdadm to build a raid1 array of 2 3TB disks, 1 partition using the entire disk.  I need to copy the data to home, but it's too much to copy over the internet, so I thought I would degrade the array and take a single RAID member home.

Twice now I have taken a disk from the array, replaced it with a blank disk and left the array happily rebuilding.

I checked to make sure that the source FS was ext4
# df -TH  | grep /dev/md
/dev/md126     ext4      3.0T  887G  2.0T  32% /mnt/data

I then brought home the removed disk, hook it up to my home machine which runs 12.04 and booted, mdadm sees the raid member and I can start up a degraded RAID 1 array with 1 device
mdadm --create --raid-devices=1 --level=1 --force /dev/md0 /dev/sdb1
and all seems good at this point.

Then I try to mount /dev/md0  and mount tells me:
wrong fs type, bad option, bad superblock on /dev/md0
...
I tried stopping the array and mounting the partition itself with 
mount -t ext4 /dev/sdb1 /mnt/data
and I get the same error message from mount

I tried to recover with backup superblocks using

mke2fs -n /dev/sdb1
then taking some of the backup block #s and passing them to
e2fsck -b BLOCKNUMBER /dev/sdb1
and it tells me
bad magic number in super-block while trying to open /dev/sdb1

When this happened 1 time, I was willing to say that somehow I damaged the disk, but twice?  I am doing something wrong.
The RAID member I left back in the source machine mounts degraded and rebuilds successfully each time.

HELP please! I need this data ASAP and I really cannot copy it at the source.

---

### Post by conradin on 2012-12-27
Can you clone the good disk with something like clonezilla?
I know that doesnt solve the issue of why the rebuild fails.
Have you checked the SMART disk integrity?

--once upon a time I had 2 disks fail at the same time. Then loads of "fun" happened.

Im assuming neither one of these disks has an OS on it, is that correct?

---

### Post by steeldriver on 2012-12-27
I think you should have used **--assemble** not **--create**

---

### Post by raygeeknyc on 2012-12-27
> **steeldriver said:**
> I think you should have used **--assemble** not **--create**



Damn - I think that you're right!  Does --create overwrite info onto the partitions?

---

### Post by raygeeknyc on 2012-12-27
OK - I am pretty sure that --create is what destroyed the FS on that disk.

Is the data written by --create localized to the point where I can recconstruct the FS metadata from the RAID partner that I still have remotely?

---

### Post by steeldriver on 2012-12-27
tbh I don't know - it would take quite a while to actually overwrite 3TB so maybe

best to wait for one of the raid gurus to stop by

---

