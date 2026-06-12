---
title: "windows not booting in grub2"
date: 2012-11-10
forum: General Help
---

### Post by Exar Kun on 2012-11-10
Hi, I have a computer with Ubuntu 12.04 and I can't boot to windows 7, every time that I selected in grub it take back to the grub menu. This is the boot-repair report [http://paste.ubuntu.com/1348907/](http://paste.ubuntu.com/1348907/)

---

### Post by oldfred on 2012-11-11
You have installed grub2's boot loader to the PBR or partition boot sector of the Windows partition. Windows has to have a Windows PBR in all NTFS partitions, not grub.

```
sda1: ______________________________________________________

    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 296189104 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You show several /grldr folders. Were you trying to use EasyBCD? I so you may want to try their forums. 

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

