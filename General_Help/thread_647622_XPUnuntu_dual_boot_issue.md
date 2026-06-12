---
title: "XP/Ununtu dual boot issue"
date: 2007-12-22
forum: General Help
---

### Post by Crypty on 2007-12-22
I installed ubuntu(gusty) a while ago to use as my main OS but I left 8GB of unpartitioned space just in case I wanted to install XP if I needed it for something.
Today I installed XP on that 8GB of space I had. The installed said i had to make it the active partition. Once I got it installed I went into the XP disk management utility through the command line and changed my Ubuntu partition back to active. I restarted and expected GRUB to present me with my choice of booting XP or Ubuntu but instead I just got a black screen with "Error loading operating system"

I don't know what to do about this so any help is appreciated. I just want Ubuntu and XP to dualboot.

Thanks.

---

### Post by davidgarcin on 2007-12-22
You need to re-install GRUB to your MBR, because XP wipes it out when it installs.

Here's some good instructions on how to do that:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once you've got GRUB reinstalled and you can boot to linux, you need to add an entry in GRUB for XP.  To do this, edit your /boot/grub/menu.lst and add an entry as follows:

title           Windows XP
rootnoverify    (hdx,y)
chainloader +1
makeactive

Where x is the number of the hard drive (numbering starts at 0), and y is the number of the partition (again, starting at zero).

-David

---

