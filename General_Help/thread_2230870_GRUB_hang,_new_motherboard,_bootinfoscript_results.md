---
title: "GRUB hang, new motherboard, bootinfoscript results attached"
date: 2014-06-21
forum: General Help
---

### Post by dmausner on 2014-06-21
New motherboard installed (gigabyte GA-Z97X-SLI), having multi-boot problem: GRUB loads Ubuntu, but hangs if selecting Windows.
(1) Does the boot info look correct? My disk1 has windows xpsp3 + 7sp1, disk2 has ubuntu. Seems like i have two GRUBs installed, one each drive.

Other factoids:
(2) No boot into Ubuntu when BIOS puts SATA in AHCI mode (hangs), boot to Ubuntu OK when SATA in IDE mode.
(3) BIOS lists each drive in both UEFI and non-UEFI mode, altho by default UEFI is disabled on the board.
(4) From Ubuntu, all NTFS partitions can be mounted and data appear to be intact.

Thanks for expertise.

---

### Post by oldfred on 2014-06-22
I would reinstall a Windows boot loader to sda, so you can directly boot Windows. That by itself will not fix Windows boot issues, but makes it easier to see issues. Grub really only boots working Windows and usually you cannot use f8 to get into Windows repairs from grub as it is too quick.

Do not run any auto fixes from Boot-Repair as that installs grub to every MBR. But you can use advanced mode and choose Windows and choose sda to install syslinux boot loader which will boot Windows. Or use a Windows repair CD or flash drive to reinstall Windows boot loader to sda.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

I converted all new drives to gpt partitioning back with 10.10 and now include both an efi partition for my new system and bios_grub for my current system. But Windows only boots from gpt partitioned drives with UEFI and UEFI requires gpt partitioning with either (or both) efi and bios_grub partitions to boot in correct boot mode.

But you show XP. I installed a SSD a couple of years ago and had to change to AHCI for trim to work. But then XP stopped working. So you must have IDE mode on to be able to boot XP. Your Windows 7 will boot with AHCI but may need driver installed if not already installed.

It became too much hassle to turn on IDE to boot XP which took 3 to 5 minutes to boot when SSD boots in 10 sec. But BIOS & grub in both cases take another 15 secs with my old system. New UEFI systems boot UEFI much quicker.

Ubuntu should boot with AHCI on? Some other setting somewhere in UEFI?

Many new UEFI systems have UEFI only, UEFI or BIOS or BIOS only settings. So if efi partition on gpt drive not found it then defaults to BIOS/CSM boot mode from MBR. That may be why you boot. 

You show lots of old kernels installed, may be time to houseclean. I let my system build to 3 or 4 and then bring it back to 2, current and one older.
      
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

    
Intel also added a lot of new kernel, support file, & video driver updates that really are only in 14.04 and some even in next kernel. With really new system, you probably would be better with 14.04, but I might install into another 20GB partition, just to test.

New 97 motherboard is on my short list of new system. Waiting for interim release of new Intel i5 chip in a couple of days. Now one new motherboard has this - AHCI&#8217;s replacement, NVMe, so IDE is extremely old, AHCI current but not the future.

      
 Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

---

### Post by dmausner on 2014-06-24
I decided to take the low road:  
- Moved Windows XP drive to old Pentium BIOS machine for full original functionality;  removed dual-boot.
- Moved Ubuntu drive to new i5 UEFI/BIOS machine in BIOS mode, upgraded 12.04 (32) to 14.04 (32).
- Will dual-boot Win7 (32) with 14.04 (32).

---

### Post by oldfred on 2014-06-24
I would suggest installing the 64 bit version if an i5 system unless you have 2GB or less of RAM.

       Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

