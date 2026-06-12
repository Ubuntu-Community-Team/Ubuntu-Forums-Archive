---
title: "Linux bootloader partition"
date: 2016-08-24
forum: General Help
---

### Post by stas7 on 2016-08-24
Good day,
I need to make a dual boot for Win7 and linux on a brand new SSD. Don't know which linux will I install, will do it later.
I need to migrate Win7 +soft from old SSD 120gb(there's only one partition) to a brand new SSD 525gb (which needs to be partitioned into 2 partitions of equal size). For migration I am going to use Acronis True Image HD. I found instructions on how to do a migration, but I don't know how to make space in the beginning for linux bootloader cause instructions advise to use Acronis True Image HD for migration and then shrink it with windows tools.
Do I need a separate partition for linux bootloader?
How much should be bootloader partition?

Does bootloader partition has to be at the very beginning of the drive?
Or is it find if it comes AFTER say windows partition?

I can connect both drives to SATA interface at the same time.
Thank you!

---

### Post by grahammechanical on 2016-08-24
I know nothing about Acronis. I do not know how it works. I can only guess that it will replicate the partition table of the old SSD onto the new SSD.

If that partition table is MBR partitioning then you will only be allowed 4 primary partitions. You will need to use 1 of the allocated 4 primary partition places as a special primary partition called an extended partition and then inside the extended partition create logical partitions to install Ubuntu in.

A lot will depend on whether Windows 7 is using 4 primary partitions or 3. Linux does not need a boot partition. Although we can have one if we so choose. With MBR partitioning the Linux boot loader (Grub) will go into the Master Boot Record (MBR) of the drive and over-write any Windows boot loader that is already there.

It is a different story if the partitioning scheme is GPT and not MBR. Then we need to know if the motherboard has a BIOS or UEFI boot system and if Windows is installed in EFI mode or BIOS/Legacy/CSM mode. I think that Windows 7 is always installed in Legacy mode on UEFI boot system motherboards.

In this case Windows will use a special bios_boot partition to put its bios boot files. That boot partition will be large enough for Ubuntu to use for its bios boot files. Both sets of boot files will reside peacefully side by side.

The situation changes again if you wish to re-use the original 120 GB SSD for Ubuntu. In this case use the Erase disk and install Ubuntu option and let the installer do the work. Just make sure that it is not going to erase the 525 GB SSD. And make sure that the Linux boot loader is going to be installed on to the 120 GB SSD and not the 525 GB SSD which it may do by default if the 525 GB SSD is sda.

Regards

---

### Post by oldfred on 2016-08-24
New systems almost never need a separate /boot partition. If very old system and drive is in IDE mode then it may not boot from beyond 137GB, also seen on some USB installs with older systems. Also full drive encryption uses a /boot partition, but then you erase Windows.
But your SSD must be in AHCI, not IDE nor RAID to enable trim, so you should not need a boot partition.

But if a UEFI install (most Windows 7 systems are old BIOS/MBR), then some mistake the ESP - efi system partition as a boot partition. It does have boot flag, but that is not the same as a BIOS boot flag. In BIOS boot flag is just to tell Windows were to find more boot code. Grub does not use boot flag.

Often when you image one drive to another, you then cannot use both drives. They have exactly the same info. In Linux you then have duplicate UUIDs and that is not allowed. And some have had Linux boot into one partition one time and the otherduplicate the next time leading to all sorts of issues. Once sure drive is imaged, disconnect or reformat old drive.

And if you have two drives connected, you can install Ubuntu to second drive. Often better to keep them separate.

---

### Post by mook765 on 2016-08-24
Nowadays we have two kinds of drives, GPT-partitioned or MBR-partitioned.
If your drive is MBR-partitioned, the bootloader will be installed in the MBR of the drive, no need for an extra "boot-loader-partition".
If your drive is GPT-partitioned and Windows is installed, then an ESP ( EFI-System-Partition ) exists and the Linux-boot-loader will be installed in the ESP, no need for an extra "boot-loader-partition".
If there is really only one partition on your old SSD it would mean that the old SSD is MBR-partitioned ( we call that "legacy mode" ). As far as I know, Win7 must be installed on a MBR-partitioned drive.
The new SSD should use MBR as well. When you install Linux after migrating Win7 to the new SSD, make sure that you boot the Linux-DVD/USB in legacy-mode.

---

### Post by stas7 on 2016-08-24
> **oldfred said:**
> If very old system and drive is in IDE mode then it may not boot from beyond 137GB, also seen on some USB installs with older systems. Also full drive encryption uses a /boot partition, but then you erase Windows.

Its a 3-year old notebook with core i5-3320. I don't use full drive encryption

> **oldfred said:**
> 
But your SSD must be in AHCI, not IDE nor RAID to enable trim, so you should not need a boot partition.


This is a setting in BIOS right?

> **oldfred said:**
> 
Often when you image one drive to another, you then cannot use both drives. They have exactly the same info. In Linux you then have duplicate UUIDs and that is not allowed. And some have 

I will move old SSD to another OLD computer right after migration.

> **grahammechanical said:**
> 
A lot will depend on whether Windows 7 is using 4 primary partitions or 3. Linux does not need a boot partition. Although we can have one if we so choose. With MBR partitioning the Linux boot loader (Grub) will go into the Master Boot Record (MBR) of the drive and over-write any Windows boot loader that is already there.


There is only one partition on old SSD.

> **grahammechanical said:**
> 
It is a different story if the partitioning scheme is GPT and not MBR. Then we need to know if the motherboard has a BIOS or UEFI boot system and if Windows is installed in EFI mode or BIOS/Legacy/CSM mode. I think that Windows 7 is always installed in Legacy mode on UEFI boot system motherboards.


The old SSD has MBR table. Though I would prefer to have GPT on new SSD. I believe motherboard is UEFI. In which mode windows installed I do not know, how can I determine this?
I migrated it 2 years ago from HDD that came with notebook using some windows utility, probably with paragon OS to SSD.

> **grahammechanical said:**
> 
In this case Windows will use a special bios_boot partition to put its bios boot files. 


No such partition.

> **grahammechanical said:**
> 
The situation changes again if you wish to re-use the original 120 GB SSD for Ubuntu. 
Regards

I do want to put Xubuntu on it and put it in another old computer.

Here is screenshot with old SSD partitioning.

> **mook765 said:**
> As far as I know, Win7 must be installed on a MBR-partitioned drive.

can somebody confirm this for sure? 
I just would prefer to use GPT on new SSD since its more flexible than MBR.

---

### Post by oldfred on 2016-08-24
You cannot easily convert a Windows BIOS install to UEFI.
Windows 7 can be installed in UEFI boot mode, but default DVD is BIOS only. You can copy to flash drive and then edit to create the /EFI/Boot/bootx64.efi files & folders to boot installer in UEFI mode.
Then how you boot install media UEFI or BIOS (both Windows & Ubuntu) is how it installs.

Windows only boots from MBR with BIOS.
Windows only boots from gpt partitioned drive with UEFI. 
So both boot mode & partitioning would have to be converted.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
[/URL]
 UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

### Post by stas7 on 2016-08-25
> **oldfred said:**
> but default DVD is BIOS only. 


what does this mean? one cannot boot from DVD in UEFI mode?

> **oldfred said:**
> 
So both boot mode & partitioning would have to be converted.


Acronis support says if I use it from bootable media via image, it should be able to convert MBR to GPT automatically. But then I will need to boot acronis in UEFI mode enforced from somewhere.
I can use either SATA DVD or put it into external USB box.

---

### Post by oldfred on 2016-08-25
Windows DVD will not boot in UEFI mode to install in UEFI mode. You have to copy to flash drive and do some minor edits.

While you can relatively easily convert a MBR drive to gpt, that does not convert an install from BIOS boot to UEFI boot. And Windows only boots from gpt with UEFI which then requires additional partitions.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

---

