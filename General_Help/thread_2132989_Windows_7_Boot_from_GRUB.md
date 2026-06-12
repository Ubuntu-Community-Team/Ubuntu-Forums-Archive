---
title: "Windows 7 Boot from GRUB"
date: 2013-04-06
forum: General Help
---

### Post by 0xc0de on 2013-04-06
Hello everyone!
I install Ubuntu in EFI mode, work perfect.
But i also have 2 partitions: Windows 7, Win 3.1(DOS).
This partitions doesn't contain EFI boot files.
I can't turn off EFI and use lagacy BIOS, because i don't have such option in settings.
If i try to boot it from GRUB2 i receive:

> drivemap command not found
Invalid EFI file path

How i can boot these OS?

---

### Post by oldfred on 2013-04-06
Windows 7 will only boot from gpt drives with UEFI, and only boots UEFI from gpt drives. XP does not even know gpt partitioning exists and will not work with gpt.
All UEFI (currently) have a BIOS/CSM/Legacy mode to allow booting older systems with BIOS mode. If your Windows 7 & XP are in BIOS mode you need to install Ubuntu in BIOS mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

