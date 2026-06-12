---
title: "DualBoot Win10/Ubuntu-Used XP Recover CD"
date: 2016-06-27
forum: General Help
---

### Post by xyz on 2016-06-27
Hello, 

As the title says it, I messed up my dual boot, esp. Win10's. I don't have a W10 Recovery CD and grabbed XP's instead, so that at the boot screen, the choice is XP or Xenial. Of course, "XP" won't boot!

I think I tried everything to fix it, Hiren's, UBCD, SysRescue, Live CD's,etc and Google.

What can be done about this? Anyone ever heard of such a stupid, embarrassing situation to be in? Thanks for reading. 
,

---

### Post by X-RED_Tech on 2016-06-27
Whatever you messed with it can only get worse if you use an old XP recovery media.
That said, what happened/happens exactly? You don't really say what is the problem...

---

### Post by xyz on 2016-06-27
Well I had W10 and Xenial's choices at boot. Having problems booting W10, I inserted XP install CD and got to r console and typed fixmbr/fixboot/exit.

This very "wise" operation seemed to have crushed a (no doubt) messed-up W10 boot and replaced it with XP's. 'Course this won't do.
```
thierry@tilleul:~$ fdisk -l
fdisk: cannot open /dev/ram0: Permission denied
fdisk: cannot open /dev/ram1: Permission denied
fdisk: cannot open /dev/ram2: Permission denied
fdisk: cannot open /dev/ram3: Permission denied
fdisk: cannot open /dev/ram4: Permission denied
fdisk: cannot open /dev/ram5: Permission denied
fdisk: cannot open /dev/ram6: Permission denied
fdisk: cannot open /dev/ram7: Permission denied
fdisk: cannot open /dev/ram8: Permission denied
fdisk: cannot open /dev/ram9: Permission denied
fdisk: cannot open /dev/ram10: Permission denied
fdisk: cannot open /dev/ram11: Permission denied
fdisk: cannot open /dev/ram12: Permission denied
fdisk: cannot open /dev/ram13: Permission denied
fdisk: cannot open /dev/ram14: Permission denied
fdisk: cannot open /dev/ram15: Permission denied
fdisk: cannot open /dev/sda: Permission denied
thierry@tilleul:~$ sudo fdisk -lu
[sudo] password for thierry: 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0deb5126

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    921661    919614   449M  7 HPFS/NTFS/exFAT
/dev/sda2          923648   1845309    921662   450M  7 HPFS/NTFS/exFAT
/dev/sda3  *      1847296 181999552 180152257  85.9G  7 HPFS/NTFS/exFAT
/dev/sda4       181999614 976769070 794769457   379G  f W95 Ext'd (LBA)
/dev/sda5  *    181999616 544283256 362283641 172.8G  7 HPFS/NTFS/exFAT
/dev/sda6  *    976156672 976769070    612399   299M  7 HPFS/NTFS/exFAT
/dev/sda7       544284672 967974911 423690240   202G 83 Linux
/dev/sda8       967976960 976142335   8165376   3.9G 82 Linux swap / Solaris

Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.


```

---

### Post by X-RED_Tech on 2016-06-27
> **xyz said:**
> Well I had W10 and Xenial's choices at boot. Having problems booting W10, I inserted XP install CD and got to r console and typed fixmbr/fixboot/exit.

Any factory installed Windows 8.x/10 is in UEFI mode so yes, by doing what you did ("fixmbr"), now you broke everything.
I really don't know what to suggest except reinstall everything??

---

### Post by yancek on 2016-06-27
With windows vista and later windows version, BCD is used as the bootloader which is totally different from the boot files used with Xp and earlier.  I'm not sure why you thought and xp recovery CD would work?  Why don't you have a windows 10 recovery CD?  Very simple to create.  It doesn't matter now as I expect you will need a full windows 10 installation DVD.

---

### Post by xyz on 2016-06-27
Thank you for paying attention to my problem.
No W10 access, no creating a recovery CD. Creating one using a Live CD would not be possible, I suppose. Wish I could go out and get a brand-new MBR.
My girlfriend uses Windows, so she's getting "nervous".

---

### Post by X-RED_Tech on 2016-06-27
Indeed. Windows 10 recovery media is something you do with a functional OS. Some vendors like HP also have their own tools for that pre-installed. If you wait until you need it it will be too late.
A moot point anyway because now you need installation media (not recovery) to reinstall everything.
However, you may also ask in Windows forums; perhaps someone can suggest something I'm not aware of (because, you know, I don't use Windows and I couldn't care less for that OS); you don't need to nor should you mention the dual-boot as it has nothing to do with your problem with Windows (then and now) but is enough to flip some heads at those forums. And/or contact the vendor's customer support as they should be able to send you the full installation media (for a fee, of course).

---

### Post by xyz on 2016-06-27
of course "for free", as usual! And maybe you don't have a "Win-Addicted" girlfriend...and I don t want to throw her out of the "Windows" but I ll probably throw some money out ot the W......

Thanks anyways.

---

### Post by oldfred on 2016-06-27
That fdisk does not work on gpt partitioned drives is not unusual. There is a new fdisk with 16.04 that does work with gpt.

Windows NTFS partitions have a backup PBR - partition boot sector. If you only ran XP repairs once, you may be able to restore a valid NTFS PBR.
       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot  

If UEFI, you boot from UEFI boot menu, not grub if Windows has issues. Windows typically needs chkdsk and you can only run that from Windows repair console. Best to have Windows repair flash drive.

I once used a Windows 7 repair flash drive to run chkdsk on my XP install. It was a better version of chkdsk as it repaired more things, but it converted my XP PBR to a Windows 7 PBR. In testdisk there also is a compare of PBR (dump) and the PBR had text saying ntldr in the XP backup and bootmgr in the Windows 7 version.

XP would not know about UEFI. And it may have installed a BIOS boot loader to MBR. But I do not think XP knows about gpt and may have totally corrupted things?

Of course the horse has left the barn, so it may be a bit late to close the barn door:
      
 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
Repair/backup/restore
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options
[/URL]
 Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)
Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

### Post by westie457 on 2016-06-27
AFAIK this can only be done from a working Windows computer to create the bootable DVD/USB media. 

[https://www.microsoft.com/en-gb/software-download/windows10ISO](https://www.microsoft.com/en-gb/software-download/windows10ISO)

Also it is free atm.

I have created a USB that will install Windows 10, 32-bit or 64-bit on one 8GB stick.

No license number is necessary when installing to a pre-installed computer because the license is stored in the 'nvram' chip.

---

### Post by yancek on 2016-06-27
If the computer was purchased with windows 10 pre-installed from one of the major manufacturers recently, you might be able to get the installation medium.  Used to be $15-$25 from HP/Dell, etc.

You can download a windows 10 90 day trial version from microsoft.  Don't know if you can then make it permanent if you have that windows sticker with the code on it?

---

### Post by xyz on 2016-06-28
Thank you all for your help. I shall investigate as soon as possible.

Haven t been around for a long while, but I was glad (not surprised) to see the community is still RIGHT HERE and ready to help out *lost souls*. Real nice.

Good day all.

---

### Post by RobGoss on 2016-06-28
Hello and welcome, At this point I'll ask you is Ubuntu installed on this machine and is it bootable?

Second, your only option here is to install Windows 10 again if you can get a installation disc I think some suggested try calling the vendor and explain that you deleted Windows some how but don't mention anything about using Linux it may void any warranties if you have it

Good luck

---

### Post by xyz on 2016-07-07
OLDFRED's links (kept'em stashed away safe) were helpful, esp. TestDisk. the Backup BS- a function I never had to use before. Dual Boot got back in order.sort of, but Win10 was in such a mess...I downloaded Win8.1 and set it up on an external hd using a friend's pc - the same we owe. 

I wanted a clean slate, so Dban Dod (Hiren's Live) did the job and proceeded to install Ubuntu on the internal hd.  Bios -on our old Dell Latitude D600- is set to boot on USB; my girlfriend is happy. Please don't ask me how I got Win8. THANKS for your support. Have a nice day.

---

