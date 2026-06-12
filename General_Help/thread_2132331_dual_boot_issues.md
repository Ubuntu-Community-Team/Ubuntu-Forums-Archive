---
title: "dual boot issues"
date: 2013-04-04
forum: General Help
---

### Post by tatmark1 on 2013-04-04
ok i got this laptop normally i run ubuntu only but since its new and i do need a windows computer i can not for the life of me figure out how to dual boot this set up...its an asus k55a-si50301
thank you very much

---

### Post by oldfred on 2013-04-04
Are you in UEFI or BIOS mode, and is your Windows a recovery install or a full new install?

If you want UEFI:
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

Windows will only boot in UEFI from gpt partitioned drives and has very specific requirements for partitions and partition order on drive.
Windows will only boot from MBR(msdos) drives in BIOS mode.
Ubuntu will boot with either UEFI or BIOS from gpt drives or BIOS from MBR drives.

---

### Post by tatmark1 on 2013-04-04
i am guessing uefi...its the factory recovery.... id like to have it like i did with 7 or xp

---

### Post by oldfred on 2013-04-04
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by tatmark1 on 2013-04-04
is there a like that can directly help me?

---

### Post by oldfred on 2013-04-04
Factory recovery normally erases drive and restores to like new. So you want to be sure to backup any info you have on system before hand.
I would have Ubuntu liveCD/DVD/Flash handy as you probably will have to totally reinstall and then restore your data.

---

### Post by tatmark1 on 2013-04-04
i dont have any thing on it. i have a live cd

---

### Post by tatmark1 on 2013-04-04
i cant even seem to get it to boot the cd so i can resize the partition

---

### Post by oldfred on 2013-04-04
Many of the new computers boot into the recovery partition and then let you restore from that. Do you still have recovery partition. A CD will not be a recovery as that has to be several DVDs.
Otherwise you need to contact vendor and see if you can get a complete recovery DVD set. Some may have a small fee for sending you the DVDs.

---

### Post by tatmark1 on 2013-04-04
so i cant do this with out the cd? screw it i just want to do a full install of ubuntu

---

### Post by tatmark1 on 2013-04-04
yes it still has the recovery partition

---

### Post by oldfred on 2013-04-04
If a UEFI system. But if only installing Ubuntu and never wanting Windows you can change to Legacy/CSM mode and boot the old fashioned way. But if you may want Windows you will need UEFI.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by tatmark1 on 2013-04-04
i got ubuntu installed screw windows

---

