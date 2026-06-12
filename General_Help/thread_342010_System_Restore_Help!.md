---
title: "System Restore Help!"
date: 2007-01-19
forum: General Help
---

### Post by Jammerwoch on 2007-01-19
**Update:** I just realized this thread is in the wron gplace.  I thought the name of this form was "Repositories & *Backups*".  I am moving it somewhere appropriate.  Is there a way to delete a thread?  I looked but wasn't able to find such a way.

Quick summary: how do I copy an Ubuntu system from a 81GB hard drive to a replacement 80GB hard drive?  The new disk needs to replace the old disk.  I am not interested in re-installing Ubuntu as I've been configuring this system for months.  Please help!  I need to have this resolved quickly.

The system drive for my Ubuntu server has started to fail, intermittently, so I got a replacement drive, booted from a Live CD (Gentoo, it's what I had lying around) and commenced to attempt to restore my pristine Ubuntu box.

I say *attempt* because I've had no success.

Part of the problem is that the new hard drive is 80GB and the failing one is 81GB (nowhere near full, though...only 8 or so GB are used).  My first attempt (which I didn't really expect to work) was to use dd: dd if=/dev/hda of=/dev/hdb.  It was a nice try, but of course dd finished early because it couldn't write that last gig.  Unsurprisingly, fdisk said the disk was messed up.

My second attempt was using fdisk to partition the drive similarly to the partitioning of the old drive, then do a 'cp -R /mnt/olddrive /mnt/newdrive'.  That went ok, but GRUB failed on bootup.  So I did a 'grub-install --root-directory=/mnt/newdrive /dev/hdb', which seemed to work.  Sure enough, when I rebooted, GRUB came up and tried to start booting Linux...and failed miserably.  I'm not in front of the computer now, so I can't remember the exact error, but it couldn't load the kernel image, and I think it said something about ext3 (all of the Linux filesystems on old drive and new are ext3).

Any help would be greatly appreciated.

Best,
  T

---

### Post by Jammerwoch on 2007-01-19
Quick summary: how do I copy an Ubuntu system from a 81GB hard drive to a replacement 80GB hard drive?  The new disk needs to replace the old disk.  I am not interested in re-installing Ubuntu as I've been configuring this system for months.  Please help!  I need to have this resolved quickly.

The system drive for my Ubuntu server has started to fail, intermittently, so I got a replacement drive, booted from a Live CD (Gentoo, it's what I had lying around) and commenced to attempt to restore my pristine Ubuntu box.

I say *attempt* because I've had no success.

Part of the problem is that the new hard drive is 80GB and the failing one is 81GB (nowhere near full, though...only 8 or so GB are used).  My first attempt (which I didn't really expect to work) was to use dd: dd if=/dev/hda of=/dev/hdb.  It was a nice try, but of course dd finished early because it couldn't write that last gig.  Unsurprisingly, fdisk said the disk was messed up.

My second attempt was using fdisk to partition the drive similarly to the partitioning of the old drive, then do a 'cp -R /mnt/olddrive /mnt/newdrive'.  That went ok, but GRUB failed on bootup.  So I did a 'grub-install --root-directory=/mnt/newdrive /dev/hdb', which seemed to work.  Sure enough, when I rebooted, GRUB came up and tried to start booting Linux...and failed miserably.  I'm not in front of the computer now, so I can't remember the exact error, but it couldn't load the kernel image, and I think it said something about ext3 (all of the Linux filesystems on old drive and new are ext3).

Any help would be greatly appreciated.

Best,
  T

---

### Post by scrooge_74 on 2007-01-19
check this link, I think the commands and the general idea should be usefull for you to copy the entire system

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

EDIT:  I think this is better [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

