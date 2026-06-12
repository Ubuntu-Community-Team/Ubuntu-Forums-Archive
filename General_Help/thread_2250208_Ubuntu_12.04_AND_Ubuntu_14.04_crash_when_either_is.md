---
title: "Ubuntu 12.04 AND Ubuntu 14.04 crash when either is in dual-boot with Windows 7"
date: 2014-10-27
forum: General Help
---

### Post by JohnFDay on 2014-10-27
I'm still "RELATIVELY" new to Ubuntu, but I've got this problem that I just can't figure out.  When I run the computer with WINDOWS ONLY, there's no boot problem.  When I run the computer with UBUNTU ONLY, again there's no problem.  However, when I load Ubuntu as a DUAL-BOOT (Windows 7, 64-bit, and UBUNTU 12.04 64-bit [and 14.04 64-bit, too] I have repeatedly had to uninstall Ubuntu to get past the boot error.  The latest attempt ended with a note about a "broken pipe", but that's not the only error I've seen.  Additionally, when Ubuntu is initially loaded, it runs fine.  The boot error only comes when I re-start the computer.

I have an HP Pavilion, from 2011, that seems to operate with no problems, and the hard disk (1 Terabyte) is less than 1 year old.  

As I said, either operating system, when it's the only one on the computer, works fine.  The problem only occurs when I've got it set up for a dual-boot.  If I have to live with one-only systems on this computer, then fine...I'll just buy another hard disk and swap between them when I want "the other" operating system.  As for "dual-boot", I've tried it with Ubuntu running "side-by-side" with Windows, and I've also tried it with the WUBI.EXE, with Ubuntu rulling "inside" Windows.  I get the boot problem no matter which way it's been installed.

Any ideas what may be the cause of these errors?   Or should I just learn to live with it?  If it has to be that way, then so be it.

Thanks in advance.
John Day

---

### Post by oldfred on 2014-10-27
There should not be any difference. 
Dual boot does not cross over from Windows to Ubuntu or vice-versa.

Broken pipe may be some driver is not correct. Often video or external device like printer, but could be any hardware driver not working or needing update.

But you could install Ubuntu to external drive or even a flash drive. Flash drives are not as speedy and may not last for a long time (good backups essential). I have a full install in my 32GB flash drive, but more for emergency boot of my laptop. Desktop has several drives and an install of Ubuntu on every drive.

---

### Post by JohnFDay on 2014-10-27
Oldfred:  Thanks much for your help.  I looked the situation over (for the umpteenth time) and have decided to put Ubuntu onto my "solid state drive", while leaving Windows 7 on the 1 terabyte hard disk.  This layout works.  All I need to do when I boot is select the disk I want to start from, and everything works "just fine".  It's a weird situation, as I described above, but at least all is well with this layout.

Again, thanks for your input!

John Day

---

### Post by oldfred on 2014-10-27
Glad you have a way to make it work. :)

I just have Ubuntu on SSD and on hard drive, with no Windows.

---

