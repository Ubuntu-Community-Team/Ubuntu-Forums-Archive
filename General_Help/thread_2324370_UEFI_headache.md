---
title: "UEFI headache"
date: 2016-05-13
forum: General Help
---

### Post by giabaio2 on 2016-05-13
Hi all,
I think I'm running out of ideas here --- and it may well be that I've missed some easy bits and making my (computer)life miserable for nothing, so I'd appreciate any help!

OK: I've got a Dell XPS 15 9550, which came with Windows pre-installed. I don't really use Windows anyway, so I installed *only* Ubuntu 16.04. I followed advice on line (eg [here]("http://ubuntuforums.org/showthread.php?t=2317843")) and did all the relevant prep (disabled secure boot, changed SATA operation from RAID to AHCI). So, all worked fine and I was able to install it on UEFI. For a few days all worked fine, but then (I *think* this may have to do with a kernel update, but I didn't keep track of this, so can't say for sure whether that was responsible for it!!), things started to go really badly. Basically, most of the times, I can't get Ubuntu (which is the only OS) to boot. When I fire up my laptop, after a few seconds I get the Dell Support Assist telling me that there are potential hardware problems. Basically, what happens is that I am not able to get to grub. If I enter the BIOS to modify the settings eg trying to add a boot option (I've seen that you sometimes need to do that), most of the times I get a warning pop-up saying that "File System Not Found!".

I can boot to a USB flash and from there, I've tried to fiddle with the /boot/efi/EFI files/settings. I've tried doing [this]("https://sites.google.com/site/easylinuxtipsproject/6"), which occasionally has worked --- meaning that after rebooting I had some success and managed to get into my Ubuntu. But the next day (or simply after a few hours), when I tried to re-boot again, I was back to square one...

I've also tried [this]("http://www.rodsbooks.com/efi-bootloaders/installation.html") (which, as I understand it --- and I may well not know what I'm doing, at this point!) instead of rebuilding the grub-efi simply copies over the files from the ESP to /boot/efi/EFI. Again, I can remember of a couple of times when this has worked, but not consistently and basically I'm not stuck with a machine that 95% of the times doesn't start up! I know I could try to re-install Ubuntu, but I've done this a couple of times already in the past month or so, and I'd really like to avoid it if I can...
Incidentally, this is the output for fdisk and gdisk --- as far as I can tell, things *are* in order: I do have a EFI partition which has a boot flag (checked in gparted) and the GPT/MBR settings seem OK...

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4C97C1CF-77C8-4EAD-8249-5868B912E1A2


Device        Start        End    Sectors   Size Type
/dev/sdb1      2048    1269759    1267712   619M EFI System
/dev/sdb2   1269760   59863039   58593280    28G Linux filesystem
/dev/sdb3  59863040   63768575    3905536   1.9G Linux swap
/dev/sdb4  63768576 1953521663 1889753088 901.1G Linux filesystem




ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.1


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4C97C1CF-77C8-4EAD-8249-5868B912E1A2
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5485 sectors (2.7 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1269759   619.0 MiB   EF00  
   2         1269760        59863039   27.9 GiB    8300  
   3        59863040        63768575   1.9 GiB     8200  
   4        63768576      1953521663   901.1 GiB   8300  

Does anybody have any idea here? 
Many thanks!
Gianluca

---

### Post by grahammechanical on 2016-05-13
I have no practical experience of that machine or any machine with a  UEFI boot system. What I know I have learnt from reading threads on this  forum.

I notice that you are providing information for sdb. What  is on sda? Also, if Windows was on sdb then it is possible that the  Windows efi boot files are still in the efi boot partition sdb1. That  may or may not be confusing the UEFI boot system. I am assuming that the  UEFI boot system is set to look to sdb for efi boot files and not sda. 

Regards

---

### Post by giabaio2 on 2016-05-13
Hi grahammechanical,
I installed Ubuntu from a USB flash drive, which was recognised as sda and so the installation ended up on sdb --- I didn't think this should matter, though? I did try overwriting the EFI/Microsoft/Boot file with a copy of the grubx64.efi --- to no avail... And yes, I have configured the machine to look for sdb using efibootmgr.

G

---

### Post by sudodus on 2016-05-13
I think the Ubuntu installer defaults to installing the EFI partition to /dev/sda even if you specify something else.

An internal drive should be found before external drives, so /dev/sda *should* be an internal drive, if there is one. But you wrote that it is not.

If you intend to install from one external drive to another external drive it can be tricky to make the target drive recognized as /dev/sda and at the same time boot from another external drive. It is often possible, but maybe not always.

An alternative in the 'all external case' is to use the method with a compressed image file described in this link: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

On the other hand, if you intend to skip Windows, and only use Ubuntu, you need not install in UEFI mode. The computer should boot and run also in BIOS mode (alias CSM alias legacy mode). In that case you should wipe the partition table and start with a new partition table, which is easy with [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe), but you can do it completely manually too with ***gparted***. A 1 TB drive can be partitioned with an MSDOS partition table as well as with a newer GUID partition table (GPT), which you have now.

Notice that with GPT you need a small partiiton with the **bios_grub** flag but without any file system for the grub bootloader in BIOS mode. See this link: [DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by oldfred on 2016-05-13
On my system and several others have posted that grub only installs to sda.
So your actual boot files for Ubuntu/grub may have installed inside the flash drive, not on the hard drive. Then boot may work with flash drive plugged in, but not when removed.

You need to make sure boot files are in /EFI/ubuntu in ESP on internal drive.
And that UEFI has correct UEFI boot entries for hard drive's ESP not ESP on flash drive.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by giabaio2 on 2016-05-13
This makes sense and probably explains why I *never* have problems booting up from my USB flash drive...
I guess the best way forward is to re-install Ubuntu making sure that it does go onto sda.

---

### Post by oldfred on 2016-05-13
But we do see some systems that promote USB flash drive to sda.

I had similar issues with both my old BIOS and newer UEFI home built systems. It turned out that I had skipped ports when installing drives. 
On BIOS system flash was sdf when plugged in, but on reboot became sdb. I had skipped port SATA1.
On UEFI system I plugged in somewhat in order but DVD was SATA1. So ports used in order, but DVD is not seen as a drive where flash drive was. So second hard drive was sdb, but UEFI/BIOS & grub saw it as hd2, not hd1 as it should be. Once I moved hard drive to SATA1 and SSD on SATA0 then things become consistent.

Or it can be a mess.

---

