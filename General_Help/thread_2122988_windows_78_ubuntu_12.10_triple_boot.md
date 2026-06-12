---
title: "windows 7/8 ubuntu 12.10 triple boot"
date: 2013-03-06
forum: General Help
---

### Post by X D face me on 2013-03-06
hello everyone

i currently have a system with windows 7 home premium and ubuntu 12.10. i want to try windows 8 but is it actually possible to install windows 8 on an allready dual-boot system without corrupting grub/mbr or ubuntu?

X D face me

---

### Post by oldfred on 2013-03-06
It will overwrite the MBR, but you just need to use liveCD/DVD/Flash drive to restore MBR.

Do you have another primary partition? Windows only boots from primary partition and normal second installs will add its boot files to the first install and have no boot files in its partition. Grub then only finds one install to boot, but Windows will update its BCD and offer both. But if you want both in grub you have to be careful how you install.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Also windows 8 is always hibernated. Dual booting can cause issues.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by X D face me on 2013-03-07
so the things i need to do are:

- make a new primary nfts partition with boot flag
- get a windows 8 live dvd
- install windows 8

will this just keep grub and my other os's? and how about my partitions, my sda1, sda2 and sda3 are allready occupied by windows, recovery and dell and my sda 4 divided in sda5 and sda6 is for linux, where should i put that new partition?

---

### Post by oldfred on 2013-03-07
If you have made a full set of recovery DVDs and a good backup, you probably can delete the recovery.

If you do not want to delete recovery and Windows 8 is just a test, then you can install it in a logical partition. But you will only ever be able to boot from the Windows 7 boot flagged partition. It will probably take over as it is the newer version, so you may want to backup your hidden Windows boot partition sda1 with Windows 7 as you will lose those otherwise?

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by X D face me on 2013-03-08
thanks, i prefer [acronis true image]("http://www.acronis.com/homecomputing/products/trueimage/#overview") for backups and i got a recovery disk for that.

---

