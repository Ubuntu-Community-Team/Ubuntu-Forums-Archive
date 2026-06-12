---
title: "100% CPU usage mount.ntfs on external harddrive formatted by Windows 8"
date: 2013-04-18
forum: General Help
---

### Post by jonashendrickx on 2013-04-18
100% CPU usage mount.ntfs on external harddrive formatted by Windows 8. It usually happens when loading two VMWare virtual machines at the same time.

FAT32 is not supported by my external hard drive and exfat is a no go at all. So question is what is the problem. Some nasty new features in NTFS on Windows 8? My teacher told me to format it on Windows 7. But it sounds so stupid.

dual boot was a solution before UEFI came.

If I install Windows 8 now first on UEFI. I get first 4 partitions for windows. But how do I partition the rest for Ubuntu? Do I need to create a additional new EFI partition for Ubuntu?

Second question if dual boot is setup, and I wish to reinstall Windows 8, Windows 8 will be installed to UEFI/EFI again, so grub is probably gone. How would I be restoring dual boot then?

---

### Post by oldfred on 2013-04-19
If you have an external drive and have UEFI, be sure to format external with gpt partitioning not the old MBR(msdos) partitioning.

You can only have one efi partition per drive, but if you may ever boot from drive, you should have an efi partition or leave room for the efi partition at the beginning of the drive. And I recommend every drive be bootable.

You can always backup efi partition, it is not large. But with efi Windows should only overwrite its folder, not other folders. Early versions of Ubuntu/grub2 with UEFI support overwrote entire efi partition which caused major issues.

But if you run the auto recovery from the system that will overwrite the entire hard drive erasing Ubuntu. May be better just to do a full backup of Windows (and efi partition).
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Only use Windows to shrink the Windows partition and reboot several times to let it run chkdsk and make repairs for its new size. And do not create partitions with Windows as it is prone to converting to dynamic partitions which do not work with Linux.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

