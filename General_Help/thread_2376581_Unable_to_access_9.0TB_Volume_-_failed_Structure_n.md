---
title: "Unable to access 9.0TB Volume - failed: Structure needs cleaning"
date: 2017-11-03
forum: General Help
---

### Post by FarSight87 on 2017-11-03
Hey guys,

Ive got a bit of a drama and need some serious advice after trying to save my RAID5 array for the last 5 days.

Ive had a mdadm RAID5 array running for nearly a year with 3x3TB hard drives. Giving me 6TB of usable space. I was running out of space so i purchased another hard drive which arrived 6 days ago. After adding the drive and booting up, i started the process of adding the drive to the array. That part seemed to run fine, with mdadm showing 4 drives active and synced etc. However, I noticed the free space hadnt increased, it had just spread the 6TB over 4 drives now instead, which i think is normally what happens until you specify to resize the new volume. 

Now I cant remember exactly what I did at this point but it involved pvresize and another command. Somewhere here everything went to crap.

I couldnt get access to my volume at this point. I think it assembles fine, but everytime i click the 9TB volume in nautilus im shown the "error mounting /dev/md0 at........... failed: Structure needs cleaning"

Naturally I googled that error and began an e2fsck of /dev/md0. It has been going for 4 or 5 days. I can see it still actually running and cloning a bunch of inodes or something at Pass 1D. But there are hundreds and sometimes i come back and it says a different amount at the Pass 1D section, meaning that its finished and done another scan while im away and got to that point again and found more inode multiply-claimed block errors or something. Seems like it might be going round and round.

I have stopped the e2fsck for now and done a few mdadm --examine --scan commands and the ouput shows "no RAID superblock on /dev/sd[bcde]1 with the line under each stating /dev/sdb1 is busy - skipping etc.

Im not sure where to go from here and could seriously use some advice. 

System details are as follows:
Ubuntu 16.04 LTS
AMD FX-6300
8GB RAM
/dev/sda1+5 Samsung 120GB SSD (operating system)
/dev/sdb1 3TB WD Green ext4 (md0 RAID5 member)
/dev/sdc1 3TB WD Red ext4 (md0 RAID5 member)
/dev/sdd1 3TB WD Red ext4 (md0 RAID5 member)
/dev/sde1 3TB WD Red ext4 (md0 RAID5 member)
/dev/sdf1 2TB Seagate (Old backup drive)

Cheers,

---

### Post by TheFu on 2017-11-03
I would wipe the disks and start over, using my backups to restore data.  RAID5 really isn't recommended for large (2TB+) HDDs, BTW.  The restore takes too long.

---

### Post by FarSight87 on 2017-11-04
Thanks for your reply TheFu.

I am currently using testdisk to copy anything important off the array. After that, Ill start from scratch and restore files.

---

### Post by TheFu on 2017-11-04
I have doubts that testdisk will get anything.  The bits of the files should be spread over multiple disks, not contiguously.
I'd use that new disk for backups, not more storage.  Nothing replaces having backups. Nothing.

I've never used pvresize in all my years using LVM.  I allocate entire disks when they are inserted into the machine to LVM, so resizing the PV/PE is never a consideration.  LVM is **very** flexible, but can be dangerous.  In 2002-ish, I lost 80% of my data because I tried to do something stupid with LVM.  Putting SW-RAID with that, and you have a recipe for issues.  

If you want storage that you don't need to understand, use ZFS in a freeNAS-like setup.  Start with 6 disks in the zpool.

---

### Post by FarSight87 on 2017-11-04
Thanks.

Testdisk seems to be working ok. Pulled nearly a terabyte off so far. A few corrupted files amongst the lot, but mostly fine. I've selected /dev/md0 as the disk to read, not the individual disks.

---

