---
title: "Can't launch windows 7 from grub"
date: 2015-11-22
forum: General Help
---

### Post by sophie8 on 2015-11-22
Hi guys,
I installed Ubuntu, choosing the option of dual boot. Now I can't launch windows from the grub, because when I select it, it only loads the grub again.
I ran the boot repair and it didn't help, here's the BootInfo summary:
[http://paste.ubuntu.com/13447815/](http://paste.ubuntu.com/13447815/)

I searched the internet for a while, but didn't find anything that could help me :\ what can I do to fix it?

---

### Post by yancek on 2015-11-22
You have a standard MBR install of both Ubuntu and windows 7.  The problem is that you have installed Grub code to the IPL of the the windows partition which I expect has overwritten the boot code needed to boot windows.  You have Grub code in the MBR and the proper files on the Ubuntu partition so I'm not sure what happened here except that is definitely not a default when installing Ubuntu/Grub.  Having overwritten the windows code and putting Grub code on the windows partition explains why you get Grub again when you select windows.  You will likely need to use your windows installation medium to reinstall windows code again.  Hopefully someone familiar with windows will come along and explain how you do that.

---

### Post by sophie8 on 2015-11-22
On no, it's worse than I thought. I swear I used the default installation for dualboot :(

---

### Post by oldfred on 2015-11-22
Windows NTFS keeps a backup. If valid relatively easy to restore with testdisk. It may say grub in PBR is valid as you can have grub in a PBR, but never in NTFS.

Otherwise you need to use testdisk "Rebuild BS" to create a "dummy" NTFS which is really the old XP type. Otherwise with grub in PBR - partition boot sector Windows will not even see it to fix it.

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

If testdisk does not work.

 Really using bootsect.exe to restore partition boot sector - PBR
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by sophie8 on 2015-11-23
Thanks for all of this info,

I tried the boot sector fix, but what I see is
 "Boot sector
 Status: OK


 Backup boot sector
 Status: Bad"

Also, I tried the windows repair guide before and after choosing the "RebuildBS" option in the testdisk. Neither worked. Maybe it's because I don't have any recovery disks for my genuine windows, so I downloaded a windows 7 torrent. It says my windows 7 version isn't compatible, and startup repair didn't help.

---

### Post by oldfred on 2015-11-23
Do not use torrents. They install virus and who knows what else.

Better to always have a Windows repairCD or flash drive for the current version you have, but you have to make that before you have trouble. Or have another computer with same 64 or 32 bit version. Or know someone with that.

You can download a legal copy of Windows, but it only is valid for 30 days without a license.

If backup was bad, then the only option is the testdisk rebuild BS, but that creates an XP boot using ntldr in PBR. chkdsk may work but better to run the bootsect.exe fix.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media


[/URL]

---

