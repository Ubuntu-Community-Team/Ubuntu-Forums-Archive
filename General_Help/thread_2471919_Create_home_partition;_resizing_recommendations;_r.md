---
title: "Create \home partition; resizing recommendations; remove 2nd FAT32 partition"
date: 2022-02-12
forum: General Help
---

### Post by ozark_hillbilly on 2022-02-12
I just finished reinstalling Ubuntu 20.04 LTS after having some CUPS issues creating a monster error log file. Don't ask...lol

I now have a second fat32 500MB (sda2) partition that is the new /boot point.
Can/should I remove/repurpose the old fat32 (sda1)?

MY 250GB sda drive has an extended (sda3) partition of 232GB with another ext4 partition inside it called sda5 (filesystem root) with the same size (232GB).
Should I rearrange sda3/sda5 before creating a new /home partition? And should I create /home with gPARTED from sda5 or use the second drive (sdb)?
I want to enalrge my SWAP area to 16 GB as I am adding another 4GB memory card for a total of 8GB RAM.
With the /home partition I was going to dedicate 40GB to it.

gPARTED & FILES screenshots are provided....

thanks for advice....

---

### Post by oldfred on 2022-02-12
If you just reinstalled, now might be the time to convert to gpt.
UEFI highly recommended gpt and Windows since 2012 only lets you install in UEFI boot mode to gpt partitioned drives.
Ubuntu does let you use MBR with UEFI, but probably should not.
As an aside, I have used only gpt with new or reformatted drives since about 2010.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

Reinstall & converting will erase entire drive, so have good backups of anything you want to keep.

There is a tool to convert without data loss (normally). But UUIDs all change so you have to reinstall grub & edit fstab at the minimum. New install may be easier. This works better on data only drives. Gparted change to gpt will totally erase drive.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by ozark_hillbilly on 2022-02-13
I will stick with what I got. I just needed some advice on best way forward to create /home partition considering my current
configuration.

---

### Post by yancek on 2022-02-13
Use gparted on your Ubuntu installation usb rather than from the installed system as you cannot modify a mounted partition.  You need to first unmount sda5, move sda3 to the left then sda5 to the left to whatever size you want.

If you are positive you are using sda2 efi, you can delete sda1.

16GB RAM is a little exxcessive, do you hibernate often?

---

### Post by Impavidus on 2022-02-13
sda1 is only 512 MB. Unless you want to reformat the drive entirely, it isn't worth the efford to do anything with it. sda2 appears unused. Is this a legacy install on mbr drive, where the installer created an efi partition anyway?

There was a rule that swap should be twice your ram. 15 years ago, when most computers had between 250 MB and 2 GB ram, that was reasonable, but it's no longer the case. You need a good reason to have more than about 4GB of swap.

When you have a separate /home partition, there's no need for the root partition to be large. You can probably shrink it to about 30 GB. That should give room for /home on sda. You don't say what sdb is used for. Where you put your /home partition is entirely up to you.

---

### Post by ozark_hillbilly on 2022-02-13
If suspend is the equivalent of hibernate, yeah, I do it all the time just to avoid start up waits.

" Is this a legacy install on mbr drive, where the installer created an efi partition anyway?"

The efi was created by the Ubuntu installation after selecting a normal installation.

I ordered another 4 GB memory card after watching my RAM usage it was getting all used up. Not a gamer or anything though.

Sdb is just a backup drive location where I run Deja Dup. My system is pretty old so having a second drive probably is not a bad idea
going forward.

I appreciate your advice as it seems reasonable and straightforward. Cheers...

---

### Post by ozark_hillbilly on 2022-02-13
"16GB RAM is a little exxcessive, do you hibernate often?"

I use suspend religiously. Lol...

Thanks for your input.

---

### Post by grahammechanical on 2022-02-13
I would like to make a point and I think that I am correct.

Both drives have MBR (Master Boot Record) partitioning table. Boot files (Grub) go into the Master Boot Record at the front of the drive. They do not go into a efi partition or BIOS boot partition. Both of those efi partitions should be empty.

With a GPT (GUID Partition Table) scheme on a drive in a BIOS (not UEFI) motherboard there will be a BIOS boot partition and an EFI system partition. Which should be empty because Ubuntu is being installed in BIOS mode and not UEFI mode and the boot files (Grub) will go into the BIOS boot partition.

I know this to be true because I have a desktop machine that has a BIOS motherboard and two hard drives. One is MBR and the other is GPT. I also have a new laptop with a UEFI motherboard and a GPT drive with Ubuntu pre-installed by the supplier in UEFI mode. The drive only has a EFI system partition for the boot files. No BIOS boot partition.

Regards

---

### Post by oldfred on 2022-02-13
If only suspending swap is not used. Only with hibernation. Suspend still keeps system in RAM. Hibernation writes RAM into swap.

Also your RAM will normally fill up as system caches recent programs loaded even when closed. Users often reload a program and then it is in RAM for quicker access. Only released with new programs need more RAM than available. Not sure of logic on what programs stay in RAM and which are released when RAM cache is full.


With gpt partitioning you need either ESP for UEFI boot or bios_grub for BIOS boot.
With MBR neither are required, but we have seen where installer may create an ESP on MBR drives.
Possibly just to make it easier later to convert to gpt as space allocated for ESP? Its just that if newer system that is UEFI, installer should install in UEFI mode only to gpt drives (like Windows does).

The only place for MBR(msdos) anymore is for older systems that only can boot Windows in BIOS mode. 
I have gpt on my old BIOS only 2006 laptop, so most older systems do not know nor care whether drive is gpt or MBR. BIOS will just jump to MBR and gpt has protective MBR.

---

