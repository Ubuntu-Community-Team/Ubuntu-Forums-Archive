---
title: "Cannot boot back into Windows, suspect it's because of shared desktop folder"
date: 2016-07-03
forum: General Help
---

### Post by yoman82 on 2016-07-03
Hi all,
I'm running into some problems with my Ubuntu installation. I'd had everything working nicely, but I today found out that I cannot boot into Windows anymore. I've been using Ubuntu for 7 or so years (across many machines), and have never had this problem before. I can select Windows 7 in GRUB, but it then says "Windows 7 failed to start", and prompts me to insert a recovery disk (I don't have this, I don't even have a CD drive). The file it cites as the issue  is \BOOT\BCD. I suspect this problem is because I am using the same desktop folder on both Windows and Linux (I configured my GNOME settings to use a folder on the mounted Windows partition as my Ubuntu desktop). This is the only change I have made on this installation versus on the previous computers I have owned, so it seems like a candidate for the issue, though I can't say for sure.
Is there any way I can fix this without the need for a recovery disk?

---

### Post by oldfred on 2016-07-04
You may just need chkdsk. But that can only be run from Windows repair console. 
Generally you should always have a repair flash drive for the current version of every operating system you have installed. Ubuntu installer makes a good repair for Ubuntu, but can only do very minor fixes to NTFS for Windows.

A few have said they were able to get into the Windows internal repair console using f8. But grub boots into Windows so fast you have no time. One user said it worked but had to almost press keys at same time and had to try many times.
May be better to temporarily restore Windows boot loader to MBR which should give more time for f8. Then when Windows is fixed restore grub boot loader to MBR.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)
Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html) 

Are you sharing files in the Windows system partition or a separate NTFS shared data partition. Better to use separate data partition separating system from data, but you still may sometimes need Windows repair tools.

If you have access to any other Windows system, you can make a repair flash drive:
       [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

