---
title: "USB Install, Windows 7, Ubuntu Shutdown Procedure"
date: 2012-12-05
forum: General Help
---

### Post by damatrix on 2012-12-05
Setup:
Special Primary MBR - Windows 7, EEPC Encryption
USB Primary MBR - Ubuntu 12.10, Installed from LiveCD

The Problem:
Both work fine, I remove the Windows 7 Drive when installing Ubuntu everything goes great install works, I boot in, setup... Sweet.

I remove the USB, insert the Windows 7 Drive works perfect.

Now when I put both in and boot into Ubuntu, on the first time that it recognizes both drives, it will work fine, but when I goto shut down all I get is a black screen. I am forced to turn it off and the problem arises where I cannot access the Windows 7 anymore.

What I have tried:

Blacklist ntfs
Fstab – noauto, nouser

But for some reason soon as I put the drive it Ubuntu Nukes my Windows 7. I understand I have a special case scenario but still Ubuntu should not be writing anything to my drive or even calling it for information. I cannot even have it see the drive where it calls a INT 19h, which is disk info. If I were to do this in windows. I would want to uninstall the drive from device manager in Ubuntu to keep it from even checking for the drive. Maybe it all screws up on boot up which would make the problem a lot harder to resolve.

Anyone? I will be surprised if I even get a response to this…

---

### Post by oldfred on 2012-12-05
Some systems promote a flash drive to sda making internal drive sdb. So that could be an issue. as then drive order is not consistent??

You also should make sure to shut Ubuntu down correctly. If not normal shut try remembering the elephants to shutdown.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

