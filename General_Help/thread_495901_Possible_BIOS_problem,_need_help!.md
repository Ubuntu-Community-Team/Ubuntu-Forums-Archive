---
title: "Possible BIOS problem, need help!"
date: 2007-07-08
forum: General Help
---

### Post by Onay on 2007-07-08
I recently installed ubuntu on an external hard drive. Now when I boot my main internal hard drive to Windows XP, or try to, I get some random text that doesn't make sense. My best guess is that the BIOS settings set my external hard drive to become the main one during installation. I attempted to fix the BIOS by restoring default settings and switching the main HD from HD 0 to HD 1, but nothing seems to fix it.

I can boot from the external hard drive, which further gives me a choice of ubuntu, ubuntu recovery, or Windows XP. I start up XP, but after a few minutes of usage I get a blue system failure message. I repeated this and it happened consistently. How can I reset my BIOS so that it will boot up my standard XP first BEFORE it boots up ubuntu? How can I restore the default settings as if the external hard drive doesn't exist?

Any help is much appreciated.

---

### Post by marshall.robert on 2007-07-08
it only a guess, i am no expert, but it sounds like the boot loader or something similar, i stumbled upon this one day [http://vista-uninstall-bootloader.freeware-alternative.uni.cc/](http://vista-uninstall-bootloader.freeware-alternative.uni.cc/) for restoring xp bootloader, you could try that and see what happens, i cant see anything bad come out of it. but be aware this is a mildly educated guess.

-rob

---

### Post by Onay on 2007-07-08
Thanks, but I discovered what the text says

```
GRUB Loading stage1.5
GRUB Loading, please wait...
Error 21
```

Someone please interpret this!

---

### Post by confused57 on 2007-07-08
You can try restoring Window's IPL to your internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Once you're able to boot your internal drive, you could use the Super Grub Disk to boot Ubuntu on your external hard drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by marshall.robert on 2007-07-08
the installer probably put grub on the internal hdd, but of course the files for grub are on the external hdd, thus causing your error. if this is correct that means that you will have to try and put grub on the mbr of your external hdd.

---

### Post by Onay on 2007-07-09
Ah, it messed up my MBR. I just found a text-based executable named MBR fix, and I restored the Windows XP boot record. Thanks for all the help everyone.

---

### Post by confused57 on 2007-07-09
> **Onay said:**
> Ah, it messed up my MBR. I just found a text-based executable named MBR fix, and I restored the Windows XP boot record. Thanks for all the help everyone.
You can use the Ubuntu live cd to install grub to the external hard drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
using the instructions, you would probably "setup (hd1)" to install grub's IPL to the USB drive's mbr...after you have done this, boot first to the external hard drive, highlight your Ubuntu entry, press "e" to edit, change root from (hd1,x) to (hd0,x)...x meaning leave this value as it is....then press "b" to boot.  This change is temporary, but can be made permanent in your /boot/grub/menu.lst.

---

