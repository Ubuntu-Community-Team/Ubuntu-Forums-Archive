---
title: "thoughts about why my flash drive is getting corrupted."
date: 2008-01-22
forum: General Help
---

### Post by miatawnt2b on 2008-01-22
I received this 1Gb flash drive at a trade show from a vendor.  The drive had some vendor sales garbage on it that I couldn't delete in windows.  So I popped the drive into my ubuntu machine and deleted the partition.  I then created a new fat32 partition with gparted, exited and mounted the flash drive.

I copied about 750Mb of mp3's to it, in ubuntu and unmounted it.  I take it to my windows XP box insert it and try to copy the data, and windows says the data is corrupt.

Hummmm... so I figure maybe gparted muffed the partition, so I put the drive back into the ubuntu machine, delete the partition, exit gparted, put the flash into the windows machine, create a new partition and format it fat32.  I then click safely remove hardware and pull the flash drive.  Put it into ubuntu, it mounts, I copy, I unmount.  Back to the windows machine.  Same thing.  Corrupt data.

What is going on?  I could understand if I wasn't unmounting, but I am clearly doing everything I am supposed to be.  Any help would be appreciated.  

-J

---

### Post by Het Irv on 2008-01-22
Did you happen to save the vendor's files, they may have included drivers or something of the sort.  Also try formating the drive in Windows and see if that helps.

---

