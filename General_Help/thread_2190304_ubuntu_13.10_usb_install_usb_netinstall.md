---
title: "ubuntu 13.10 usb install/ usb netinstall"
date: 2013-11-26
forum: General Help
---

### Post by spiritech on 2013-11-26
i am having problems installing ubuntu 13.10 form my usb. i normally do it and it works fine. i download the main 64bit PC (AMD64) release from here 

```
http://releases.ubuntu.com/saucy/
```

i have used both "start up disk creator" and "Unetbootin" to make a bootable usb stick, "start up disk creator" has only completed once and when i try booting all i get is a blinking cursor. "Unetbootin" completes every time, however when i select install, nothing happens.

if i download the mini.iso for a netinstall, and create a usb stick using that. i can complete the install proccess from the usb. problem is that ubuntu will only boot if i keep the usb stick plugged in if i remove it and try and boot from HDD all i get is a blinking cursor.

i have tried manually selecting where to put the boot loader during the install and select the master boot record and i still get the same result.

spiritech

---

### Post by sydney2 on 2013-11-27
Hi, 
Well it seems its a graphics issue. Which graphics card are u using ? Please post the output of lspci -vnn . Secondly how are u preparing your USB for Unetbootin to boot your iso ? At times the mbr plays prank & booting gets stuck either with a boot error or a blinking cursor. You had also mentioned that for Untubootin when u click install nothing happens, well are u able to execute it live?

Sydney2

---

### Post by spiritech on 2013-11-27
> **sydney2 said:**
> Hi, 
Well it seems its a graphics issue. Which graphics card are u using ? Please post the output of lspci -vnn . 

output from lspci -vnn is, i assume it is the graphics card section you wanted.

```
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV790 [Radeon HD 4890] [1002:9460] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited Device [174b:e115]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fbfe0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at e000 [size=256]
    Expansion ROM at fbfc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
```

> **sydney2 said:**
> Secondly how are u preparing your USB for Unetbootin to boot your iso ? 

Usb is clean formatted to fat32 using "disks" facility.

> **sydney2 said:**
> At times the mbr plays prank & booting gets stuck either with a boot error or a blinking cursor. You had also mentioned that for Untubootin when u click install nothing happens, well are u able to execute it live? 

no all i get is the options screen, anything i select after that results in command line propmt

intrframs$

or somthing like that, not 100% sure.

i am pretty sure that all that is happening is that the grub is being installed onto the usb and not the hdd. i have checked and found the grub on the usb at.

/corsair16gb/boot/grub - contains

/corsair16gb/boot/grub/efi.img
/corsair16gb/boot/grub/font.pf2
/corsair16gb/boot/grub/grub.cfg
/corsair16gb/boot/grub/loopback.cfg

and - /corsair16gb/EFI/BOOT contains

/corsair16gb/EFI/BOOT/BOOTx64.EFI
/corsair16gb/EFI/BOOT/grubx64.efi

i assume these files should be on the hdd and not on the usb.

---

### Post by sydney2 on 2013-11-28
It seems u may have ended up in installing grub 2 to the USB & its gpt? or in case of the intrframs$ it could be that your program is failing with its procedure while creating our bootable USB, it could be that the kernel is getting corrupted or the root file system.Secondly which OS distro was previously installed on your machine. Thirdly as for the blinking cursor it seems your HDD partitioning scheme is wiped off or corrupted. If is is possible try to take your HDD to a friend' s place and view its properties using a disk utility like gdisk on a Linux distro. It should be with a gpt partitioning table with at least one EFI System Partition & rest as data partitions. As for the USB alter its partitioning table scheme to gpt for maximum compatibility with again an EFI a System partition formatted with FAT32. Similarly try to stick to the default installation procedure while installing Ubuntu. Make sure u correctly identify your disk while your installing i.e. between sda, sda1 sdb sdb1. It could be your selecting your usb and since your installation files are on it it might be getting overwritten or something like that..

Well try out the above solutions & keep me posted........

Sydney2

---

