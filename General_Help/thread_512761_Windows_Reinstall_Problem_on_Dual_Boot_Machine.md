---
title: "Windows Reinstall Problem on Dual Boot Machine"
date: 2007-07-29
forum: General Help
---

### Post by DougS on 2007-07-29
This may be more of a Windows problem (sorry) but I don't want to lose the other 2 partitions (Data & Ubuntu) if possible.

Dual boot has been working really well with Grub.

Windows installation corrupted during a defrag so deleted using Gparted...

I now have (approx):
30GB Data partition (FAT 32)
24 GB Ubuntu partition
100 GB ex-Windows partition (now unallocated)
I had hoped to simply (joke) delete Windows partition, reinstall in same space, use Super Grub CD to get back to dual boot Grub set up but...

When I try to re-install (arrogant) Windows, it asks if I want to install in an (Unknown) 130 GB partition which SOUNDS like it is going to go ahead and use the Unallocated AND the FAT32 Data partition which I would rather it didn't

I didn't dare to proceed past this point in the installer.

Any ideas why it seems to see the spare space as the 100GB unallocated plus (apparently) the 30 GB Data partition.

Or am I missing something?

---

### Post by Paul S on 2007-07-30
I thought all windows had to be first on the drive.  How did you ever get it installed in 3rd place originally?  Anyway, you should be able to limit it to the first partition by creating and formatting an empty linux on partition 3.

HTH

---

### Post by DougS on 2007-07-31
Thanks for that.

Thread now closed because:

As it happens, I tried to check and double check this but Windows went ahead and deleted the data partition finally ended up having to format from scratch - not sure why, thank goodness for a backup of data.

Have also had trouble getting back to original configuration so a disk image will be made ASAP to prevent the time needed to restore all programs on both systems in the future.

It was VERY noticeable how easy it was to restore Ubuntu (with all apps and updates) compared to Windows, although Feisty Grub seems to ignore Windows, this will need to be checked as I get more experienced with dual boot etc...

Regards
Doug

---

### Post by stchman on 2007-07-31
> **DougS said:**
> This may be more of a Windows problem (sorry) but I don't want to lose the other 2 partitions (Data & Ubuntu) if possible.

Dual boot has been working really well with Grub.

Windows installation corrupted during a defrag so deleted using Gparted...

I now have (approx):
30GB Data partition (FAT 32)
24 GB Ubuntu partition
100 GB ex-Windows partition (now unallocated)
I had hoped to simply (joke) delete Windows partition, reinstall in same space, use Super Grub CD to get back to dual boot Grub set up but...

When I try to re-install (arrogant) Windows, it asks if I want to install in an (Unknown) 130 GB partition which SOUNDS like it is going to go ahead and use the Unallocated AND the FAT32 Data partition which I would rather it didn't

I didn't dare to proceed past this point in the installer.

Any ideas why it seems to see the spare space as the 100GB unallocated plus (apparently) the 30 GB Data partition.

Or am I missing something?

Yes select the unallocated partition and XP install will ask you to format the partition to either NTFS or FAT32.

Once Windows is done you will have to reinstall GRUB.

---

