---
title: "Help me in Installing Ubuntu"
date: 2013-06-26
forum: General Help
---

### Post by ThulasiS on 2013-06-26
Hi I am new user to Linux.I am trying to install Ubuntu 12.10 along with my windows but I could not? When ever I am clicking install Ubuntu inside windows the DVD ejecting from tray automatically and saying Please remove the bootable media from tray and press ENTER.Why it happening so?Even I tried to install Ubuntu 10.10 into my system in new drive apart from windows it was giving the message no root files found, try with partition table again some thing like this it was coming why it happening so? I need to install it with out losing my data help me in this regardThanks in advance

---

### Post by oldfred on 2013-06-26
Wubi now only installs from inside Windows. And since all new computers use UEFI with gpt partitioning wubi is being discontinued as it does not work with the gpt partitioning required with UEFI.

You cannot easily install 10.10 as it is not now supported, so no updates are available. Better to install either the long term support version 12.04.2 or the newest 13.04.

Any time you install a new system there is a chance of error. Often user error clicking on the wrong thing. Also hard drives or systems fail, so it data is really valuable you must have good backups.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by ThulasiS on 2013-07-01
Thank you So much
I'll try with new version of Ubuntu..
I'll go for windows back up before installing new version of Ubuntu.
Thank u again

---

