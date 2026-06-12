---
title: "Installing Ubuntu 13.10 on a laptop that already has W8 and openSuse 13.1..."
date: 2013-12-07
forum: General Help
---

### Post by andrew.t.sullivan on 2013-12-07
Hello

I've just bought a new laptop which, inevitably, came with W8 installed.  That software is everything I expected!

I have, after some trouble, installed openSuse 13.1 in a dual boot configuration - I used this distribution because I had a lot of trouble with later versions (10.04 on I think) crashing on my old PC.  I would, however, like to give U 13.10a fair try, so I just tried to install it as part of a "triple boot" setup.  I got as far as the point where the installer offered to install Ubuntu "alongside openSuse 13.1", and chickened out.

Could anyone explain what the installer would actually do under these circumstances?  I'm loathe to break the installation I have at the moment (which for information, has openSuse installed in UEFI mode with Secure boot enabled).

TIA

Andrew

---

### Post by dragonfly41 on 2013-12-07
i would not push your luck further by going for a triple boot.

If you have an external drive or flash drive available for use you can use unetbootin to prepare a bootable [COLOR=#2f4f4f]**external**[/COLOR] Ubuntu.

Then select BIOS in your laptop to boot Ubuntu from USB.

This avoids any tampering with Windows+openSuse.

p.s. You can install unetbootin on either Windows or Linux.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

p.p.s.  At this stage of dabbling with a new laptop I would prepare a Windows 8 rescue disk as first priority.

---

### Post by oldfred on 2013-12-07
I agree on rescue disk and full Windows backups. 
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/

[/URL]
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

I always partition in advance as I want to know what sizes and where Ubuntu is going to put things. Usually I do not want default install of / (root) and swap anyway. You still have to use Something Else and select partition, format, mount point to install whether you create partitions are part of manual install or in advance.

I do not have UEFI, but you do have to make sure you boot Ubuntu installer in UEFI mode. If you have secure boot on then it will only boot in that mode and will install in that mode.
I do prefer to have different operating systems on different drives where possible.




[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]
[/URL]

---

### Post by andrew.t.sullivan on 2013-12-07
Thanks for that, I think you're right, I would be pushing my luck!  I'll try running 13.10 from a large usb stick.

I made a rescue disc (on an external drive!) before doing any dabbling.

Andrew

---

### Post by andrew.t.sullivan on 2013-12-17
Brief update...

I was feeling lucky (some might say foolhardy!) this afternoon and tried the triple boot with Ubuntu 13.10.  I chose "Something else" in the disk partitioning screen, created separate partitions for Root and Home, made sure the installer was going to mount the existing Swap and EFI partitions (which t was) and hit Install.  I did all this without an internet connection (deliberately).  It all went smoothly and when I rebooted I got a Ubuntu-style Grub screen with Ubuntu, openSuse and W8.1 listed, and they all work!  The only glitch was that when booting Ubuntu I got a message saying that KVM was disabled in BIOS.  I went into BIOS and activated this, message has gone away.

FWIW so far I quite like 13.10.

Andrew

---

