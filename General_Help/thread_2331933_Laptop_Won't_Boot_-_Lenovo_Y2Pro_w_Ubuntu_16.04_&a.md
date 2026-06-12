---
title: "Laptop Won't Boot - Lenovo Y2Pro w/ Ubuntu 16.04 &amp; Windows 10"
date: 2016-07-26
forum: General Help
---

### Post by biggydrink on 2016-07-26
Hi all,

First thing's first--my boot-repair report: [http://paste.ubuntu.com/20645244/](http://paste.ubuntu.com/20645244/)

I recently installed Ubuntu 16.04 on my Lenovo Yoga 2 Pro as part of a Linux class I was taking. Near the end of the semester I did a project about GRUB, and tried manually configuring a bootable USB stick with GRUB. However... I did not really understand what I was doing, and ended up screwing up my bootloader somehow so that now the computer does not boot--I have to use a USB stick, also running Ubuntu, ver 14,04 (which I already had prior to trying to make my own).

I've tried installing GRUB again to /dev/sda, and I've tried the boot-repair utility, and since screwing things up I've done a lot more research into booting computers in general, but I haven't been able to fix things yet, so I'm looking for some help from anyone who might know what to try next. I do not know what exactly I did that caused the problem, although if I remember right, I unmounted sda2 (in Ubuntu), remounted it somewhere else, could not unmount it again, and then restarted. I might be wrong on some of the details though, it's now been about two weeks. According to this page, sda2 is the computer's factory UEFI boot partition.

A few notes:

[LIST]
[*]All my old files are visible and available when I boot using a USB, so I think it's only the bootloader, MBR, or boot partition that's been messed up.
[*]My computer is a Lenovo Yoga 2 Pro with Windows 10 (upgraded from Windows 8), which I then installed Ubuntu on to.
[*]I have backups of everything and I could re-install Windows, then re-install Ubuntu, and use all the backups, but I would prefer to fix the problem (maybe learn something along the way).
[*]Lenovo shipped this laptop with 7 partitions (sda1 - sda7), and I've since added 3 more - sda8, my Ubuntu partition; sda9, a linux-swap partition, not sure exactly what it does; sda10, a a new BIOS_GRUB partition that boot-repair required me to make.
[*]More information about the Lenovo factory partitions can be found here: [http://www.lionhack.com/2013/12/25/lenovo-yoga-2-pro-partitions/](http://www.lionhack.com/2013/12/25/lenovo-yoga-2-pro-partitions/)
[*]Apparently the typical factory
[*]Before I broke things, I was booting into GRUB 2 with options to load Ubuntu or Windows, plus some recovery boots.
[*]Right after I broke my bootloader, the computer booted into the Lenovo OneKey recovery system, and the BIOS did not show ANY bootable internal drives.
[*]After running boot-repair, the internal drive shows as bootable, but if I boot into it I get only a blinking cursor.
[*]My ideal end goal is a dual-boot machine with both Ubuntu and Windows 10. 
[/LIST]


I'm willing to try almost anything, since my only backup plan is to wipe and reinstall anyway, and I have backups of my data. Any help is very much appreciated!

---

### Post by yancek on 2016-07-26
You have mixed MBR with UEFI which doesn't work.  Your boot repair shows Grub in the MBR of both drives.  It also shows an EFI partition.  You are using GPT partitioning so that means you need to use UEFI for windows.  The BIOS boot partition is only needed if you do an MBR install with GPT partitioning on Linux.  Since you need UEFI for windows with GPT, there is no need for this partition.  I don't know enough about UEFI to offer a solution but you do not seem to have any Ubuntu efi files on that partition.

---

### Post by grahammechanical on 2016-07-26
I am basing my comments on the boot Repair Summary.

When Windows 8/10 is installed in EFI mode then Ubuntu must be installed in EFI mode. And in your case, Windows 8 is indeed installed in EFI mode But Ubuntu is installed in BIOS/Legacy/CSM mode.

When the hard drive has GPT partitioning and the OS is installed in EFI mode there has to be an efi_boot partition . It is the place where the OS efi boot files go. In your case it is sda3 and you can see the Microsoft boot files in sda3.

When the hard drive has GPT partitioning and the OS is installed in BIOS/Legacy/CSM mode then there has to be a bios_boot partition for the boot files to go. In your case sda8 is a BIOS boot partition and grub is installed in it. And sda10 is also listed as a bios_boot partition. What is more sdb3 seems to be an efi_boot partition with a Ubuntu efi boot file in it. Or, one of the Ubuntu efi boot files. I seem to remember there are about 3 different Ubuntu efi boot files. Although I suspect that only one may be needed.

But sdb seems to have MBR partitioning as it has an Extended partition. And the swap partition is on sda9.

So things are really mixed up. I suggest that you plan out how you want to use the second hard disk. Whether you want Ubuntu on sda or sdb and think about reinstalling. Tidy up the partitions. Reinstall Ubuntu in EFI mode. And let the installer put the Ubuntu efi boot files in sda3 alongside the Windows boot files and set the boot order to boot from sda.

Regards.

---

