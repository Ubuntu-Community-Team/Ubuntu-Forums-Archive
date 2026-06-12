---
title: "Adding XP hdd to Dapper system?"
date: 2007-06-19
forum: General Help
---

### Post by tparker on 2007-06-19
My computer currently has one hard drive that is running Ubuntu. I have a second hard drive that already has XP installed on one partition of it and an ancient Red Hat on the other partition (that I do not need).

I need to find out how to add the XP drive to the system and make it give me the option of which drive to use at boot (preferably defaulting to the Ubuntu drive) without reinstalling the operating system on either drive. The dual boot on the XP drive was set up years ago by someone else for me, I have no experience with setting up dual booting either on the same drive or, as I need now, on multiple drives.

Both hard drives work fine on their own, but I am very tired of physically opening the machine and trading the cables around each time I need to switch drives. The only thing I need the XP drive for is City of Heroes, which refuses to work under WINE (Cedega is not an option). 

If it matters for how to do this:
both drives are ATA
Ubuntu drive is running Dapper AMD64
mainboard is ASUS A8N-SLI deluxe

---

### Post by Sonofmoog on 2007-06-19
Look into BootItNG.  It is a Windows boot loader that will boot both Windows and Linux.  It isn't free, but it's worth twice what you'll pay for it.   

You could run update-grub /dev(location of bootloader).  You could get lucky, and it'll find your Windows partition ..

You can also hand-edit menu.lst to boot the XP drive.  Your boot menu might look like this:

title Windows XP
root (hd1,0)
makeactive
chainloader +1

Be aware that this advice comes from a Linux newbie, and proceed with caution ..  HTH

---

### Post by firstlife on 2007-06-19
Word of CAUTION!!!!

I understand you aren't going to be reinstalling Windows, but I wanted to point out that IF you decide to reinstall windows, it will make itself the default os, and you will either need to do a recovery of your linux os boot capabilities, or reinstall the linux os. Windows likes to mess up other os'es boot capabilities.

Ok, enough with the warnings you shouldn't need.  The best thing I can think of is to make your linux os boot first, or be the primary drive, and windows as the slave/second cable. Add the above line (you can do it right from the boot loader by pressing "e" for grub or "alt" + t??? for lilo. Cant remember exacly.)

Note that this may not work. This is because windows is very picky of where it resides in your system.  (It likes to be first in line)  It has to do with the registry, and other things which I don't have time to tell you about right now. So try this setup, and let me know how it goes.

By the way, this info is for someone with some experience with linux and windows. So if you don't understand, let me know and I will explain it more in depth. Not a problem.

---

### Post by confused57 on 2007-06-19
> **tparker said:**
> My computer currently has one hard drive that is running Ubuntu. I have a second hard drive that already has XP installed on one partition of it and an ancient Red Hat on the other partition (that I do not need).

I need to find out how to add the XP drive to the system and make it give me the option of which drive to use at boot (preferably defaulting to the Ubuntu drive) without reinstalling the operating system on either drive. The dual boot on the XP drive was set up years ago by someone else for me, I have no experience with setting up dual booting either on the same drive or, as I need now, on multiple drives.

Both hard drives work fine on their own, but I am very tired of physically opening the machine and trading the cables around each time I need to switch drives. The only thing I need the XP drive for is City of Heroes, which refuses to work under WINE (Cedega is not an option). 

If it matters for how to do this:
both drives are ATA
Ubuntu drive is running Dapper AMD64
mainboard is ASUS A8N-SLI deluxe
This might be an option for you:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Just connect your Ubuntu as master drive &  Window's drive as slave...then add an entry to grub to boot Windows...

---

