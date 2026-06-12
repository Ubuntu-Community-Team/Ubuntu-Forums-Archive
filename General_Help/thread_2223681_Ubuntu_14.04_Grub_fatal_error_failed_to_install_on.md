---
title: "Ubuntu 14.04: Grub fatal error: failed to install ond /dev/sda; RAID0"
date: 2014-05-12
forum: General Help
---

### Post by kellen2 on 2014-05-12
Hey guys,
Im really having a hard time installing Ubuntu 14.04 on my computer right now

Hardware:
Intel I5 3750k CPU
asrock extreme4 z77 chipset
16 gb ddr3 kingston (i think) 1333 clock speed
nvidia gtx570
2tb WD Hard drives RAID0 config (Array setup by my motherboard)

Error:
Grub failed to install on /dev/sda: Fatal Error

Im trying to install onto a clean array, so there is currently no OS on it. I previously had Xubuntu 14.04 installed on it and Windows 8.1 before that. I originally tried to install ubuntu 14.04 on my 
computer while windows 8.1 was on it, but I was getting the same error. As a result I tried Xubuntu 14.04 and it succesfully installed (don't know why it is working but Ubuntu 14.04 isn't).
Anyways, I'm trying to get a better handle on linux, and this seemed like a challenge so I'm trying to tackle this installation of Ubuntu 14.04 now. 
The installation goes error free until it gets to the bootloader installation. I tried directing it to install on the RAID0 array instead of the individual hard drive mounted as /sda and the error disappears when I instruct it to do so, but when I reboot, I get nothing but the "_" on a black screen after the bios screen. 

If anyone has any ideas, you'd be a big help, thanks

*Edit1

Just noticed that Ubuntu has the full 2tb RAID setup and the first harddisk /sda (1tb) mounted at the same time. This doesn't make sense to me since that is supersampling the /sda hard drive as its space is included in the RAID and as its own entity. Not sure if this can help

---

### Post by oldfred on 2014-05-12
I do not know RAID, other than some issues that installing grub has.

Are you installing with BIOS or UEFI boot mode? The other installs that I have seen usually had the efi partition outside the RAID.

Not sure if 14.04 desktop installer has RAID drivers. With 12.04 you had to use the alternative installer for RAID or LVM and they then stopped releasing the alternative installer and said they would add that to the desktop installer. I see the LVM is now an option with desktop, but do not see RAID.

If you have the desktop version, run BootInfo report. Or download the full Boot-Repair CD.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
Some other Asrock threads.
 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by kellen2 on 2014-05-13
Thanks for the reply!

Looks like ubuntu 14.04 doesn't support raid configurations. I took the two hard drives off raid and the installation went flawlessly. Kind of a bummer though

---

### Post by oldfred on 2014-05-13
You probably can add RAID drivers after the fact. 
Or use the server installer and add the desktop to that. 
Either way you end up with exactly the same system with a bit of effort.

---

