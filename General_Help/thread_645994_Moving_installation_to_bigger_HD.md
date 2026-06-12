---
title: "Moving installation to bigger HD"
date: 2007-12-20
forum: General Help
---

### Post by PinkFloyd102489 on 2007-12-20
I checked some of the similar threads and will detail my findings.


In another thread, it was suggested to use ghost4linux. I made the boot CD from the iso but before I did that, I prepared the HD. Im currently have Gutsy installed on a 10GB HD. I have anywhere between 3.5 and 4 free, depending on what Im doing. I have a 20GB HD that I would like to move my current installation to.

I used Gparted to create a primary ReiserFS partition with 1.5GB for swap. Booted into G4L and selected to clone from /dev/hde1 to /dev/sda1. sda1 is in an external case, which Im moving to and hde1 is my current disk.

G4L reported a successful clone and was detected by the BIOS. But when GRUB went to boot, it said OS not found.



Any ideas?

---

### Post by Z_o-s-o on 2007-12-20
New harddrives usually come with a CD that can be booted and you can move over everyhting....

Its worked for several times on XP

---

### Post by logos34 on 2007-12-20
> **PinkFloyd102489 said:**
> I used Gparted to create a primary ReiserFS partition with 1.5GB for swap. Booted into G4L and selected to clone from /dev/hde1 to /dev/sda1. sda1 is in an external case, which Im moving to and hde1 is my current disk.

G4L reported a successful clone and was detected by the BIOS. But when GRUB went to boot, it said OS not found.

Either you're still booting to grub on the internal hard disk (error because you deleted hde1), or you're booting to the external drive but forgot to edit menu.lst or something.  

Does you Bios support usb boot?  I'm guessing from those small drive that this is an older pc...if so usb boot might not be an option.  But if it is you should [put grub on the mbr of the external drive]("http://ubuntuforums.org/showthread.php?t=224351") and set the bios to boot straight from that.

---

### Post by PinkFloyd102489 on 2007-12-20
I thought copying everything over from hde1 to sda1 would accomplish GRUB, but I guess not. This is a 10 year old computer, so no USB boot. I removed the bigger HD from the external shell and swapped it with the old one.


I'll try installing GRUB into the MBR of the bigger drive.

---

### Post by logos34 on 2007-12-20
> **PinkFloyd102489 said:**
> I thought copying everything over from hde1 to sda1 would accomplish GRUB, but I guess not. This is a 10 year old computer, so no USB boot. I removed the bigger HD from the external shell and swapped it with the old one.

I'll try installing GRUB into the MBR of the bigger drive.

Just as I suspected.  In that case, installing grub to mbr of external won't help.  You'll have to create a grub /boot partition on hde and put the kernel images there, then reinstall grub the hde's mbr.  So you'll boot to grub on the internal, which will load the kernel and then you'll operate from root on the external.
See[ this guide]("https://help.ubuntu.com/community/BootFromUSB") (--> section 'Booting kernel form internal hard drive').

---

### Post by PinkFloyd102489 on 2007-12-20
Ok, installing GRUB allowed me to boot the drive but I have a new problem now.


The old drive had about 6GB taken up. Now that Ive cloned to this drive, there should be 6GB taken up on it also. That's not the case though. It shows 14GB used with 3.5GB free, same as the old drive. 1.5GB is devoted to swap, so there's 19GB in all.

Did the Ghost4Linux do this or am I missing something?

---

### Post by logos34 on 2007-12-21
1 GB actually = 1.073 billion bytes (so figure on ~ 18.6 gb)

But I'm not sure about the 14 gigs used space (?)...that's a big discrepancy.  I've never used ghost4linux (I like partimage, clonezilla, dd), so I can't say.  

**df** 

is showing that?

---

### Post by PinkFloyd102489 on 2007-12-21
Ok I downloaded Clonezilla, so Im going to put the new HD back in the external shell and try it later. I need to buy some CD-Rs first. *rolls eyes*

---

