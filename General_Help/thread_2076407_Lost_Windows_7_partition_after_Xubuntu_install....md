---
title: "Lost Windows 7 partition after Xubuntu install..."
date: 2012-10-25
forum: General Help
---

### Post by smlrwd on 2012-10-25
I partitioned the drive from within windows to install Xubuntu. 
I then install Xubuntu and everything seems to go well.

Grub shows the Ubuntu boot potions and the Windows 7 Recovery option but not my Windows 7 OS option. 

Attached is the file from the boot info script found online while trying to fix this.

Worst case, can someone at least tell me how to read the files on the partition and copy off files I want to keep and I can do a clean install. It probably needs it anyway.

Thanks

---

### Post by Moose on 2012-10-25
I'm currently at school but when i get home in about 2 hours, pm me your menu.lst file. I will edit it so that it includes your Windows 7 OS. But you will have to include in your PM a few things...
 
1: What partitions are your OS's installed on. Usually Windows is SDA1 and Linux SDA2.. If its different tell me that..
 
and 2 your drive letters ..

---

### Post by smlrwd on 2012-10-25
So... where is the menu.lst file? I thought it was in boot/grub but it's not.

Edit: Ok, it's called grub.cfg now.

---

### Post by oldfred on 2012-10-26
Script was not able to mount sda2, partition table says it is NTFS.

That often occurs as the Linux NTFS driver will not mount a NTFS partition that needs chkdsk to prevent further damage that chkdsk may not then be able to fix.

You need a Windows RepairCD. Did you make one from your install? If you do not have it, you can make one from any Windows 7 that is either 32 or 64 bit whichever yours is. 

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Always run chkdsk and run again until there are no errors, that may be all that is required
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
Vista, but 7 is the same.
[https://kb.wisc.edu/page.php?id=6565](https://kb.wisc.edu/page.php?id=6565)

Then after Windows is repaired, run this from Ubuntu terminal which will add a Windows boot entry to grub.cfg.

sudo update-grub

---

