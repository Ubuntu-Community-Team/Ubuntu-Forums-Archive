---
title: "cant boot to xp &amp; ubuntu can't see drive space"
date: 2012-11-10
forum: General Help
---

### Post by greatsirkain on 2012-11-10
when I installed 12.04 it asked if I wanted to keep windows xp as a boot option, I said ok and halved the hard drive space between ubuntu and winxp but at boot if I click on windows the boot menu just resets and the countdown to automatically boot to ubuntu restarts. In ubuntu the hard drive is listed as half its actual size and booting from another hard drive from either windows or ubuntu still only shows the half the hard drive...Any thoughts on where the other half is?

---

### Post by oldfred on 2012-11-10
It may just be unallocated? Or Was Windows on that drive? To see details:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by greatsirkain on 2012-11-11
master SATA hard drive 1 with wixp pro, keyboard freezes at boot so I can't log in.

master IDE hard drive 2 with Ubuntu & winxp, Ubuntu works fine but windows wont boot
the missing half of the drive is the space I allocated to the existing winxp install. I think Ubuntu  gave me the option to encrypt the xp home folder or something during set up too.

boot repair output:
[http://paste.ubuntu.com/1351824/](http://paste.ubuntu.com/1351824/)

---

### Post by oldfred on 2012-11-11
Second one today with grub installed to Windows partition.

```
sda1: __________________
    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 199669304 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

```[http://ubuntuforums.org/showthread.php?t=2082847](http://ubuntuforums.org/showthread.php?t=2082847)

You have installed grub2's boot loader to the PBR or partition boot  sector of the Windows partition. Windows has to have a Windows PBR in  all NTFS partitions, not grub.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by greatsirkain on 2012-11-12
Thanks for the help but still no joy

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK
Backup boot sector
Status: Bad
Sectors are not identical.

The sourceforge page says I'll have to use fixboot from a windows cd...Bit tricky because even bios doesn't recognise my dvd drive. I'll try get that fixed if there's nothing else I can try?

---

### Post by oldfred on 2012-11-12
Testdisk also has a rebuildBS that creates a new boot sector that is compatible with XP. 
But you are still going to have to run chkdsk from an XP disk.

---

### Post by greatsirkain on 2012-11-13
Yup, I tried the rebuildBS and it just added the broken version of winxp from the other hard drive to the grub list (which actually did boot just it doesn't work). Then I tried Xen to see if I could get Ubuntu to boot with the broken version of windows so I could get in to do repairs but I must have done something wrong because I couldn't even get Xen to boot Ubuntu, the screen just went all mental then the system rebooted. 

Although I think know what you meant when you said is it unallocated because the half of of hard drive that shows up IS the windows partition, the half that vanished is the current ubuntu with an encrypted home folder I think...Oops...It's all very confusing

Think I'll try using someone else's working computer to make a live usb of xp. I wouldn't use windows at all but Wine just doesn't work with some of the things I need

---

### Post by oldfred on 2012-11-13
If it is encrypted it will not show.

Encryption converts data, so then partition tools cannot see data inside as it is encrypted. Only the partition table shows that it still is a partition or boot into the system that encrypted it and decrypt it to see the data.

---

### Post by greatsirkain on 2012-11-13
makes sense then that no other operating systems I've tried can see the  missing 100gb from the hard drive but Ubuntu loads up with the option to  mount the extra 100gb, I get you. And the only way I can fix my winXP  boot is with a winXP disk.

Not going to risk breaking Ubuntu,  I'll do a format & fresh intall of XP on my other hard drive &  use this windows partition as junk space, thanks again for the help!

---

### Post by greatsirkain on 2012-11-14
hirensbootcd fixed everything, some serious virtual lovin to whoever Hiren is.

---

