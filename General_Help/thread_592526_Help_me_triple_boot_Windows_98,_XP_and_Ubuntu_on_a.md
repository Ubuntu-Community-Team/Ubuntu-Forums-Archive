---
title: "Help me triple boot Windows 98, XP and Ubuntu on a single drive"
date: 2007-10-26
forum: General Help
---

### Post by hurtstotalktoyou on 2007-10-26
Okay, folks.  This is a little bit strange, I know, but I do need some help.  My computer has a single hard disk drive (80GB), on which I must find a way to install three distinct operating systems:

Windows 98 First Edition
Windows XP Home Edition
Ubuntu Studio 7.10

I thought I knew how to do this.  I thought I'd just install 98FE first, then XP, then Ubuntu Studio (with Grub).  Simple, right?  Apparently not.

Windows 98 and XP installed just fine, but I noticed that XP forced its own bootloader onto the drive (which is fine, I guess).  So up to that point everything was working great.  I had a dual-boot Windows 98FE and Windows XP Home, and both OSes loaded perfectly.

Then I tried to install Ubuntu Studio, which caused major problems.  First, Grub only detected Windows XP, not Windows 98.  However, when I tried to load XP from Grub, it took me to the Windows bootloader instead (where I get to choose between 98 and XP).  From there, choosing 98 worked fine, and it loaded nicely.  Yet trying to load Windows XP resulted in the following error message:

[i]Windows could not start because the following file is missing or corrupt:
<Windows root>\System32\Hal.dll.
Please re-install a copy of the above file.[/i]

Not knowing how to fix "Hal.dll," I tried simply re-installing XP.  That fixed XP, but it also destroyed Grub, so that I can't get into Ubuntu.

So, what's my problem, here?  Any help would be much appreciated!

---

### Post by nacho32 on 2007-10-26
[here is a link to restore the grub after windows wiped it out]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

1 got a 3 boot os to work
1 xp
2 vista 
3 ubuntu

I had 2 hard drives, so 80 gigs might be a little small for 3 os system you might want to get another HD
tools you want google them super grub boot loader and g-parted must have tools

now when I choose other os in boot loader it will bring up the 2 choices earleir windows or vista, I'm not sure if xp will give you that choice to go to 98, 
you all might want to check youtube out their or google videos I found alot of help how to's their

---

### Post by anaconda on 2007-10-26
You just need to reinstall grub, because XP install wrote over it. 

search the forums with:
restoring grub after windows install

---

### Post by strabes on 2007-10-26
Follow the GRUB link in my signature.

---

