---
title: "How to make USB stick"
date: 2016-03-30
forum: General Help
---

### Post by dryan775 on 2016-03-30
Ok, here's my problem.

I had an older Non-PAE laptop with 10.04 on a failing hard drive.  I would boot it from a 8GB USB2.0 stick with 10.04LTS with persistence and an encrypted home folder.  Worked great.
The computer was dying so I copied all my stuff off the stick and wiped it.

The new laptop has PAE and I wanted to update the stick to 14.04LTS again with persistence and encrypted home folder.

Wiped the stick, did a full install (under LiveDVD).  It corrupted the Grup ON THE HARD DRIVE so I could not load my 14.04 partition (only had options for Windows and Stick).  
Used boot-repair to fix the hard drive grub so I can one again boot to my Windows or Ubuntu 14.04 partitions with the stick removed.

Appears there is no grub on the USB stick itself.  Now when I try to boot to the stick, i just get "checking media,", short pause, "fail" and it goes back to the hard drive grub.

Question:
How can I install Ubuntu 14.04LTS on a stick from my system WITHOUT messing up the hard drive's grub and have the stick have it's own grub (I want to be able to boot it on another computer as needed, not just mine)?   Do I need to run the full install to the stick again?

I'm sure there's a simple step or checkbox I need to click during the process that I missed.

Thanks in advance!

---

### Post by C.S.Cameron on 2016-03-31
I prefer unplugging the hard drive before doing a full install to USB.
If you can't do that, use "something else" when partitioning and  confirm boot loader is installed on the root of the USB drive.

---

### Post by sudodus on 2016-03-31
What do you want on your USB stick?

***- Installed system, installed like into an internal drive, but to the USB stick***

See this link: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

> It is a two step procedure: Make a CD/DVD/USB boot drive, boot from it and install into a[nother] USB pendrive. ***Make sure that you install the bootloader into the head of the target pendrive*** (not into the internal drive or the source pendrive and not into a partition). Install almost like you would do (into an internal drive), but into the pendrive. It is **easier, if you remove the internal drive, otherwise** you must use **Something else** at the partitioning window and point the bootloader into the pendrive. Otherwise it will be installed into the internal drive /dev/sda.


***- Persistent live system (a live system with a partition with the label casper-rw for the persistence)***

See this link: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

