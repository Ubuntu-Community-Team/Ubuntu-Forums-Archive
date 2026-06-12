---
title: "Grub doesnt run Windows /"
date: 2014-08-02
forum: General Help
---

### Post by rebeca2 on 2014-08-02
Hello everybody. I have finished the instalation of Ubuntu 14.04 TLS in my computer.

The problem is that when I restar my computer, in the grub window, appears Ubuntu and WIndows. But when I select Windows, it returns again to the grub window, and I cant run Windows.

Anyone knows  how can I repair this?

If you need something information, tell me please^^

---

### Post by oldfred on 2014-08-02
Boot-Repair cannot fix most Windows issues, but you can run the BootInfo report and post the link so we can see if otherwise correctly configured.
Grub really only boots working Windows.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rebeca2 on 2014-08-02
[http://paste.ubuntu.com/7937797/](http://paste.ubuntu.com/7937797/)

This is the log of Boot Info

---

### Post by oldfred on 2014-08-02
You cannot install grub2 to partitions, particularly NTFS partitions as they have essential Windows boot info.
But NTFS keeps a backup and you can use testdisk to restore backup.
Not even sure why they still offer NTFS as a option for grub to install.

      >  sda1: _______________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type: [COLOR=#ff0000] Grub2[/COLOR] (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 492710264 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.

    

Boot Sector must be NTFS or Windows not grub.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR Similar instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If backup is also bad, then you have to have a Windows repair CD or flash drive to run bootsect.exe in Windows repair console.

Edit - first link does not work anymore. You can use the BootSectorFix link.
It looks like the extra instructions for various repairs that were created by the developer of BootInfoScript have been removed.

---

