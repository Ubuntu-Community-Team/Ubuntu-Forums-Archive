---
title: "Dual booting a Toshiba Tecra R840 running windows 7 with Ubuntu"
date: 2014-12-01
forum: General Help
---

### Post by alopex38 on 2014-12-01
Recently bought a Toshiba Tecra R840- would like to dual boot this [running windows7] with Ubuntu - or maybe even replace windows with Ubuntu.

Have read that this is difficult/impossible - is this true - if yes is there any way around it?  not by using Wubi - [tried this had problems]

Hippocrat

---

### Post by nerdtron on 2014-12-01
The best way is to boot into live mode and try for yourself.

But I think you'll have problems because of the AMD graphics card on that machine.

---

### Post by oldfred on 2014-12-01
Is system UEFI or BIOS, only a few Windows 7 systems used UEFI, but many newer systems with Windows 7 are actually UEFI based hardware using the BIOS/CSM boot mode.

Download the 64 bit version of Ubuntu and install to a flash drive. Boot flash drive in live mode and see how it works and what may not work straight out of the box.

 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
But that is with Windows 8 and secure boot. Windows 7 does not have secure boot.

But I would make sure you have updated BIOS to latest version from Toshiba.
And make good backups of Windows and make a Windows repair flash drive. You should have these even if not installing another operating system.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

