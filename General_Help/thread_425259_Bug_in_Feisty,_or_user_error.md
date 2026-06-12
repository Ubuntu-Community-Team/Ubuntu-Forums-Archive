---
title: "Bug in Feisty, or user error?"
date: 2007-04-27
forum: General Help
---

### Post by niall111 on 2007-04-27
I spent a lot of time trying to get around this, so i'm fairly confident it's a bug, but maybe someone can correct me.  If it IS a bug, could someone point me to where i have to report such things?


In my system of 3 hard drives, all SATA 160GB drives, I had a drive (sdc) that had been partitioned to 90gb of ext3 space, and the rest left unpartitioned.  I purposely left this drive out my /etc/fstab file, so that it wouldn't be mounted, and installed gparted on my system to try and repartition the drive.  I deleted the 90gb ext3 partition, which left the full drive at 160gb of unpartitioned space.  This is where it gets funky.

When i attempted to create a new partition on this drive, of type FAT32 (later I tried using ext3, same results), as soon as gparted attempted to create the partition, Ubuntu somehow auto mounted the drive!  This is apparently some new feature, which i suppose would be neat for new users who don't know how to mess with fstab?  Why it would wait until partitioning begins to auto mount the drive is a mystery though.  So once the drive was auto mounted, of course the partitioning failed because the drive is now mounted!  I took a look at my /etc/fstab file again at this point, but nothing had been added there.  Perhaps it's possible that auto mounting drives is an option somewhere in Feisty that I haven't been able to find?  

So being unable to partition from my installed version of Feisty, i booted up the LiveCD and tried it from there, with the exact same results.  The LiveCD also auto mounts any drive it can find, but at first it did NOT mount this particular drive! (still sdc of course)  At this point i noticed that it also thinks it's the full 160gb size, when that 90gb partition was never that size!  With some help from the #ubuntu support channel in IRC, i tried doing the partitioning with fdisk on the liveCD, but that also yielded the same results.

Finally, my only option was to boot up an Edgy liveCD and do the partitioning there, which worked flawlessly.  Does anyone have any ideas for something I may have missed here?  The main issue/bug with this whole thing is Feisty somehow only auto mounting the drive once partitioning begins...

---

### Post by osxdude on 2007-04-27
I noticed that if you open the drive in the File Browser, it auto mounts there. Maybe that's why my partitioning is failing for me.

I'll look into it. I'm going to start my comp now. (My other one.)

EDIT: I found it. It's in GNOME Volume Properities, under the settings menu. Problem solved?

---

