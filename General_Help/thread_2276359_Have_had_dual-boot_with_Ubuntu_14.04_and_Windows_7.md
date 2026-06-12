---
title: "Have had dual-boot with Ubuntu 14.04 and Windows 7 for a while, Windows no longer boo"
date: 2015-05-01
forum: General Help
---

### Post by rulison on 2015-05-01
Hey everyone,

I'm working on a Lenovo Thinkpad W530.  I installed Ubuntu 14.04 in a dual-boot last Fall, and only now am I having problems starting Windows.  It also failed to start once a month ago, but worked fine after a restart.  When I select Windows, my computer either restarts itself or loads Windows Startup Repair.  I have no external devices plugged in.

-I've run Startup Repair 12 times now, it now usually says "Windows cannot repair this computer automatically."

-I've also tried system restore, but every previous image it loaded still doesn't boot.

-Ubuntu still works.  I tried running boot-repair, and got the following output: [http://paste.ubuntu.com/10967407/](http://paste.ubuntu.com/10967407/)

-I also tried Method 1 from this: [http://www.sevenforums.com/tutorials/139810-sfc-scannow-run-command-prompt-boot.html](http://www.sevenforums.com/tutorials/139810-sfc-scannow-run-command-prompt-boot.html)
It found a problem, but couldn't fix it.  I'm uploading the log, but that'll take a while.

Anything else I can try?  If there's more info I could provide that might help, please let me know.

Thanks!

---

### Post by efflandt on 2015-05-02
Besides a service pack a long time ago, there was a Win7 update some time this year (not sure exactly when because I rarely boot Windows at home) that would fail if booting from grub. It would spend a long time updating during shutdown then a long time on reboot, then the update would fail and it would spend a long time reverting everything back. But I have grub on sdb (SSD with small Ubuntu system for emergencies) and standard Windows mbr on sda, so for me it was simply a matter of temporarily changing the boot drive in BIOS for the Windows update to succeed. But unless you interrupted the update process, the update failure did not cause a Windows boot failure, it just resulted in a failed update.

So maybe you have some other issue like some sort of sector failure in the Windows portion of your drive. I had to replace a drive in my desktop about a year ago, but it only started failing at the far end of the drive in my Linux partition and did not affect Win7. So I was able to clone Windows to a new drive (after shrinking its main partition from within Windows to make more room for Linux), reinstall Ubuntu fresh, then copy my /home directory over from the old drive. Only a few game files were corrupted which Linux Steam was able to replace by checking integrity of game cache.

---

### Post by rulison on 2015-05-02
Hm, now that you mention it the first system restore option was from a back-up made after a "critical update," so a Windows update could definitely have been the problem.  What exactly should I do?

---

### Post by oldfred on 2015-05-02
Often if Windows has issues booting thru grub adds to them. Grub really only boots a working Windows.
I might temporarily restore a Windows boot loader with either your Windows repair flash drive or Boot-Repair, see if you can fix Windows and then use Boot-Repair to restore grub.

Did you set Windows system partition as read/write in fstab? That can lead to issues. 
The Linux NTFS driver exposes all hidden files & folders. 

Back with XP (before dual boot) as a knowledgeable user I always turned on showing all those hidden files & folders and regularly broke Windows. Often I would try to click on a folder while still moving mouse and some some essential folder to another place. Once I learned that was an issue I often was able to fix that type of error.

Best to have a separate NTFS data partition as read/write and just have Windows system partition as read only.

---

### Post by rulison on 2015-05-02
Thanks for helping.  How do I use boot-repair to restore the Windows boot loader?

---

### Post by oldfred on 2015-05-02
Generally better to use Windows to fix Windows.

But Boot-Repair's advance mode lets you choose an operating system and the drive to install a boot loader into. Due to legal issues it cannot install the official Windows boot loader, but installs syslinux which works just like Windows from MBR. Windows boot loaders just look for partition with boot flag and jump to partition with boot flag and more Windows boot code in PBR or partition boot sector.

---

### Post by rulison on 2015-05-03
Ok I restored the Windows loader and can now boot Windows!  I'm gonna reinstall GRUB from the Ubuntu installation CD.  Thanks oldfred and efflandt!

---

### Post by oldfred on 2015-05-03
IF Windows is working best to make a repair CD or flash drive, now.

       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

