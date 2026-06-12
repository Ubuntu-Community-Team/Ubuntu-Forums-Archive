---
title: "Having trouble with Windows 8 after installing Ubuntu 64-bit"
date: 2012-12-12
forum: General Help
---

### Post by NoOneRuleZ on 2012-12-12
Here is what my partition looked like yesterday morning:

[100 mb system partition] [499.9 gb partition for Windows 8]

I ran disk manager and reduced the Windows 8 partition. Then, I had:

[100 mb system partition] [479.9 gb partition for Windows 8] [20 gb partition free space]

Then, I installed Ubuntu from a usb stick (I selected install Ubuntu alongside Windows 8), and now my partitions look like this: [http://i47.tinypic.com/2pt3yxe.png](http://i47.tinypic.com/2pt3yxe.png)

My Linux works fine, but when I selected Windows 8 in grub, I get this:

> error: device format "ldm/442e8310-28d1-11e1-90b1-e0cb4eb65983/Volume2" invalid: must be (f|h)dN, with 0 <= N < 128.

Press any key to continue...


followed by:

> A disk read error occurred
Press Ctrl+Alt+Del to restart

Specs:

960t
4 gb ram
560 ti

---

### Post by oldfred on 2012-12-12
Windows 8 is always in some hibernation state unless you totally turn it off. Did you attempt to write something from Ubuntu into Windows?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
You can try f8 right after pressing Windows entry in grub, but others have reported that it is very quick compared to a boot from MBR. Or you have to try several times and it may still not work.

Otherwise you need a Windows 8 repairCD or flash drive and see if you can run repairs from that.
       Windows 7 repair USB, Also Vista if service pack installed

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by NoOneRuleZ on 2012-12-12
> **oldfred said:**
> Windows 8 is always in some hibernation state unless you totally turn it off. Did you attempt to write something from Ubuntu into Windows?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

    
You can try f8 right after pressing Windows entry in grub, but others have reported that it is very quick compared to a boot from MBR. Or you have to try several times and it may still not work.

Otherwise you need a Windows 8 repairCD or flash drive and see if you can run repairs from that.
       Windows 7 repair USB, Also Vista if service pack installed

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Why do I need to press F8 after selecting Windows 8 in grub?

---

### Post by oldfred on 2012-12-12
It may get you into a Windows repair screen. Otherwise you have to use a Windows repairCD or flash drive.

---

### Post by Corelogik on 2012-12-12
I ran into a couple problems when installing Ubuntu to it's own partition along side windows 7. I found the solution to be to write the boot loader to /dev/sda instead of /dev/sda1

If you write the boot loader to the windows partition, it can and probably will give you errors trying to load windows when selected from the grub menu.

I had to repair the Windows boot loader and re-install a couple of times to figure it out. Give it a try. As for Windows 8 specific help, afraid I can;t help you there as I refuse to use that craptastic abortion of a UI.

---

