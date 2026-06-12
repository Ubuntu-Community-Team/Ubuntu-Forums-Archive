---
title: "Problem partitioning T23 IBM Thinkpad"
date: 2006-07-21
forum: General Help
---

### Post by xenomorph99 on 2006-07-21
Hi,

I'm having a problem partitioning this device.

I've already installed Windows 2000 on the laptop (NTFS) then followed up with Ubuntu 6.06.

The partitioner correctly sees one NTFS partition of 28GB which I tried to resize to 15GB then added an extended partition with 4.5GB (root), 6GB (home), 2GB (Dos) & 768MB Swap but the partitioner failed when attempting to resize the original partition.

I then tried with the boot option "floppy=thinkpad" appended to the boot option and had exactly the same report "cannot resize...", although when I retried to just got a blank dialog.

Do I need to upgrade the bios etc or should it work as it is?

The other option that I suppose i have is to try to partition it with Knoppix or Gparted...

Any help would be appreciated. I did a quick search about but most threads just say that the Thinkpads are linux friendly and appear to have no specific issues.

Ta,
Xeno

---

### Post by Paerez on 2006-07-21
This isn't a thinkpad issue, its just an issue with your partitions. I would try Gparted (or qtparted under knoppix) or PartitionMagic in windows.

---

### Post by xenomorph99 on 2006-07-21
I've not had any trouble partitioning any other PC I've installed Ubuntu on, though (possibly 6 different ones). OK, so they didn't necessarily have a 28GB NTFS partition but they all had Windows 2000 or XP installed on a single NTFS partition immediately followed by Ubuntu.

Ta,
Xeno

---

### Post by Paerez on 2006-07-21
It may just be the way the partition table was written on this computer. I would try running fdisk on the drive and pressing P to get partition info. See if any errors crop up.

---

### Post by stimpsonjcat on 2006-07-22
Did you defrag the NTFS partition before trying to resize?

---

### Post by xenomorph99 on 2006-07-22
Hi,

No, I didn't...but I'd only just installed Windows 2000 so I don't think it would be very fragmented.

I've since tried to use gparted standalone to repartition but that didn't work either so I used fdisk to create the partitions I wanted, then reinstalled Win2k and am installing Ubuntu now. 

I would have posted the error report from gparted/ubuntu but I suppose it is in some log file somewhere than I'll never find so I suppose we'll never know what was wrong.

Ta,
Xeno

---

