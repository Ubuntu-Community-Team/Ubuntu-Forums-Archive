---
title: "Dual Boot - MBR to GPT What can I expect?"
date: 2020-07-03
forum: General Help
---

### Post by maddenjmf on 2020-07-03
Quite simple, I have windows 10 2004 installed.

MBR, Legacy bios. I installed Ubuntu 20.04 alongside Windows in this mode.

Now I want to change MBR to GPT via the built in Windows command, and change my settings in BIOS to UEFI (supported on my machine).

My question is, is the only complication that the GRUB bootloader will be lost (and need to be repaired after), or could there be bigger complications?

When I created the live USB installation media, I remember I selected an option for MBR installation for Linux and don't know if this will also cause issues with the conversion.

Thanks!

---

### Post by crip720 on 2020-07-03
Probably a clean install of both OSs with loss of data.  This is something to be done before installing OS, not after.  Windows and Ubuntu will work well the way they are setup now.  You need a better reason than it can be done, to do it.

---

### Post by maddenjmf on 2020-07-03
That would be the tidy way I agree. The main reason is that I have 25GB unallocated space that I want to use to create a partition (and therefore make available). It was a years old ASUS factory image that's no longer needed due to the Windows 10 restore image includes within the OS.

I am limited to 4 primary partitions with MBR and by converting to GPT I would be able to tidy it up and allocate the dead space for use either for Linux or Windows.

---

### Post by crip720 on 2020-07-03
Do not need to convert to add space to one or both OSs, but be aware that working on partitions can be bad for data(not always but a chance).  Nicest way is to copy or backup important data to another drive and start over if you want GPT.   If not use Windows tools/programs to add to Windows and Linux tools for Ubuntu.  Ubuntu will need to be done from live USB, it has to be unmounted to work partitions.  Depending on position of unallocated space it might need to be moved.  Should be at right of partition to be added to.

---

### Post by maddenjmf on 2020-07-03
That's my problem, it is at the very beginning of partition table, followed by Windows c:

So let's say I'm trying to add unallocated space to Windows (which I am), I use Windows tools or programs to move free space to the right of another partition that could be expanded ... But I cannot move because it is unallocated space, and I cannot allocate space (and move) because I have already max 4 primary partitions!

This is why the question I asked convert to GPT but from what I understand of you explaining, reinstall is my only option because the second option I cant get to work even with windows programs like AOMEI

---

### Post by crip720 on 2020-07-03
Two questions, do you need the extra space or it just bothers you it is there?  Do you have important data that you can't lose?  Adding space from the right is easier and safer for data, but if data is backup and have windows repair disk handy, should be able to move windows to the left.  This might make windows unbootable till you use repair disk, data also might be a mess.  No guarantee that windows will not need a re install even with repair disk.

  Your data is the most important consideration before doing this, it can and probably will be lost.

---

### Post by oldfred on 2020-07-03
Windows only installs & boots in BIOS mode from MBR partitioned drives and only in UEFI boot mode from gpt partitioned drives. Also required partitions with Windows are significantly different. 
Best to backup all your data & just reinstall.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)


Ubuntu can be more easily converted if gpt to start with. With UEFI/gpt you do need an ESP, but only have to then re-install grub to convert from BIOS to UEFI, if drive was gpt. 

But UUIDs all change if drive was MBR which then changes some other settings. Backup & re-install will save a lot of reconfiguration.

---

### Post by grahammechanical on 2020-07-03
I am speaking from a Linux point of view but I guess that it must be the same from a Windows point of view:

We cannot move unallocated space but we can expand a partition to take up all the unallocated space and then shrink the partition so that the unallocated space is now behind that partition. In this way we eventually get the unallocated space behind all the partitions. 

The truth is that with a 4 partition limit one of those partitions has to be deleted and then the allocation of one new partition be used to create a special primary partiton called an extended partition. Having used all the unallocated space (including the space from the deleted partition) to make the extended partition we can then create as many primary partitions as we like inside that extended partition.

I have 2 drives. I has GPT.  The other has MBR. The MBR partition drive has 1 primary partition and 1 extended partition and inside the extended partition there are five more primary partitions.

Without the possibility of increasing the number of partitions beyond 4 by using an extended partition we would never have been able to dual boot with Microsoft Windows at all and Linux as a desktop OS might never have survived. People might not be aware of it but they pay for the OS when the buy the machine. Who wants to scrap something they paid good money for? The ability to dual boot has kept the goal of a Linux desktop OS alive and practical.

Also remember that we are viewing the partitions on a drive from a linear point of view but the drive is a disc. The placement of the boundaries of partitions and the data in them is not linear on a circular disc. What we are changing is the Index of where on the disc a boundary is and where the data is.

Regards

---

### Post by kneutron on 2020-07-04
--I'm going to chime in here and say that **the only way to do this safely is with a 2nd disk**.  I recently redid all the partitions on my 1TB laptop drive and documented exactly where partitions started/ended, and how I wanted things to look afterward, before making any changes. Then I backed up all my data to an external 1TB drive. 

--You should seriously do a bare-metal backup with AOMEI or Veeam (or Acronis or the like) to a separate disk before redoing your partition layout, and *be prepared to reinstall Windows and/or Linux afterward*.  This means having pre-burned install media for both to ISO/DVD or USB.  Trust me on this, because if something goes wrong you don't want to be left with no restore/reinstall options.

---

### Post by kneutron on 2020-07-04
> [COLOR=#000000]Without the possibility of increasing the number of partitions beyond 4 by using an extended partition we would never have been able to dual boot with Microsoft Windows at all and Linux as a desktop OS might never have survived

--I feel you man, but even back in the IDE days there was always the possibility of adding a 2nd drive just for Linux ;-) and ever since USB2 it's been doable to boot Linux from an external drive and run with decent speed.  Also much better now that we have external SSDs to replace crappy thumbdrives.[/COLOR]

---

