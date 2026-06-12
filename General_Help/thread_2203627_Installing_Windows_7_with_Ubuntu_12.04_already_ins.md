---
title: "Installing Windows 7 with Ubuntu 12.04 already installed."
date: 2014-02-04
forum: General Help
---

### Post by PotatoHead007 on 2014-02-04
Hey guys :) 
I have a UEFI Samsung, but it is in legacy mode ever since i deleted Windows 8(had to spend a month with it before i found out how to dual-boot with UEFI).
I want to install Windows 7, for my games(games that are a **real **pain in wine), but i do not know how to install Windows without it messing up my Ubuntu 12.04.
I heard that one way is to create a partition, and then just install Windows 7 on that? Can anyone please comfirm this, or tell me how to do it?
I am quite good with commands, so you don't have to explain too well :) Really need this though. And i have no ext HDD to install Windows on.

---

### Post by oldfred on 2014-02-04
Windows 7 can be installed in BIOS or UEFI, but to use UEFI you have to copy to flash drive and make a few changes. Windows only boots with UEFI from gpt partitioned drives. 
If you converted Ubuntu to BIOS boot, drive could be either MBR or gpt as Ubuntu works in BIOS mode from either partition scheme.

If system is only BIOS/MBR is it just like any old dual boot install. But all the old MBR issues are still there. You can only have 4 primary partitions and Windows only boots from a primary partition formatted NTFS and with boot flag. You can install to one primary NTFS partition although default installs use two, one 100MB boot and main instal. Part of reason for separate boot was so you could encrypt main install as boot files can be encrypted and to have recovery(repair) console in separate partitions as you might be able to run fixes if main partition is corrupted. Still better to have Windows repairCD or flash drive.

Post this to see partitioning:

sudo parted -l

---

### Post by PotatoHead007 on 2014-02-05
Hey :)

Output:
```

Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  746GB  746GB   primary   ext4            boot
 2      746GB   750GB  3980MB  extended
 5      746GB   750GB  3980MB  logical   linux-swap(v1)

```

If i understand you correctly, i should make a partition(i would make it 150GB), formatted as NTFS with a boot flag?
Thanks for your help :)

---

### Post by oldfred on 2014-02-05
You have only used two of the 4 primary partitions sda1 & the extended sda2 which also counts as a primary.
So shrink sda1 by the amount of space you need, but not too small as all systems need some extra space.

You have to use gparted from live installer as you cannot modify partitions that are mounted. You also have to click on swap and swap off as live installer usually uses swap to speed up install.
       Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

    
If dual booting I might make two NTFS partitions, A somewhat smaller 30 to 50GB for Windows system with the boot flag and another NTFS for data. Then from Linux you can read/write from data partition but configure to only read from Windows system partition. That helps avoid issues as Windows does not like too much activity from outside its own system. 

Not sure if NTFS from gparted always works. Some have reported that they then had to reformat again with Windows and set active again. But Windows will not see partition to install unless you have boot flag. Move it from sda1 as only one partition can have boot flag per hard drive.
Windows should install into  the unallocated but will make its two partitions. And Windows often corrupts partition table and will overwrite MBR, so best to have current version Ubuntu live installer to reinstall grub to MBR. And make back ups of partition table, so if corrupted you can restore it. Usually a bigger issue if Linux partition is inside the extended as a logical, so you may be ok.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

After creating NTFS partition with gparted.

 Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by PotatoHead007 on 2014-02-05
Oky, will try when i have time, thanks again :)

---

### Post by PotatoHead007 on 2014-02-06
**EDIT: **I got a 120GB HDD! Will do some digging on how to install Win7 on an ext HDD :)

---

### Post by oldfred on 2014-02-06
windows does not install to external drives only internal drives.

---

