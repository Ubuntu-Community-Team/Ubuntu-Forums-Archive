---
title: "Can I boot from the Ubuntu Live CD to an installed Ubuntu on my 2nd hard drive?"
date: 2008-05-25
forum: General Help
---

### Post by JavaChet on 2008-05-25
Please excuse me if this topic has been discussed before. I am a new subscriber and was a bit overwhelmed by the number of posts to search to see if the answer already exists. If so, please point me to it and I will be very grateful. Anyway, here is my question:

I recently removed GRUB from the MBR on my primary hard drive. The Primary Drive has Windows XP (I know, I also wish it didn't) and my second hard drive is dedicated to Ubuntu. I was dual-booting very nicely, but I now want to be able to remove or disconnect the Ubuntu drive and when I tried it the GRUB sector in my MBR would fail.

So I restored my MBR to boot only windows but I would still like to boot into my 2nd hard drive to run Ubuntu from time to time and have not found a way to do this without re-installing GRUB into the MBR of my Primary Drive.

Isn't there some way (bootable diskette with the GRUB code on it, or by booting the Live Ubuntu CD first and then using it to "activate" the Ubuntu system on my hard drive, or some other way) to bypass the "normal" boot into Windows and go right to Ubuntu when I want to? In other words, a complete emulation of the GRUB code that is called / activated in the MBR but only residing on a bootable diskette or CDROM eather than in the MBR of the Primary Drive.

I don't have the expertise to figure this out for myself but would appreciate any help from the Ubuntu community.

Thanks. Chet Skapczynski (JavaChet)

---

### Post by TeoBigusGeekus on 2008-05-25
Can't think of another way... What was wrong with grub?

---

### Post by bwhite82 on 2008-05-25
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB)
[http://linux-sxs.org/administration/grubflop.html](http://linux-sxs.org/administration/grubflop.html)

---

### Post by confused57 on 2008-05-25
You could also try Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your bios can be set to boot first to the Ubuntu drive, you can install grub to the drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the above link, but it would be something like:
```
root (hd1,0)
setup (hd1)
```
Boot first to your Ubuntu drive, if you get a grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot...this is if Ubuntu is on the first partition of the Ubuntu drive(2nd partition would be (hd1,1), which you would change to (hd0,1)).
This is temporary if it works, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```

You could then add a grub entry to boot Windows on your other drive, e.g.:
```
title  Windows 
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

This way you wouldn't need to use a boot floppy or cd to boot Ubuntu...if Ubuntu fails to boot for some reason, just change your bios boot order to boot Windows.

---

### Post by JavaChet on 2008-05-26
> **TeoBigusGeekus said:**
> Can't think of another way... What was wrong with grub?

Actually GRUB worked fine. It's just that I want to be able to remove the Secondary hard drive with UBUNTU on it from my system and move it to another computer or simply put it back into the system at will and boot UBUNTU whenever it pleases me. With GRUB in the Primary MBR I couldn't do that. Some of these other solutions below may help me do that.

Thanks for replying.

---

### Post by JavaChet on 2008-05-26
> **Soldierboy said:**
> [http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#GRUB)
[http://linux-sxs.org/administration/grubflop.html](http://linux-sxs.org/administration/grubflop.html)

Thank you. Those links bear some studying which I will do very soon.

---

### Post by JavaChet on 2008-05-26
> **confused57 said:**
> You could also try Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If your bios can be set to boot first to the Ubuntu drive, you can install grub to the drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the above link, but it would be something like:
```
root (hd1,0)
setup (hd1)
```
Boot first to your Ubuntu drive, if you get a grub boot menu, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot...this is if Ubuntu is on the first partition of the Ubuntu drive(2nd partition would be (hd1,1), which you would change to (hd0,1)).
This is temporary if it works, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```

You could then add a grub entry to boot Windows on your other drive, e.g.:
```
title  Windows 
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

This way you wouldn't need to use a boot floppy or cd to boot Ubuntu...if Ubuntu fails to boot for some reason, just change your bios boot order to boot Windows.

Thanks. I will also investigate the Super GRUB link. I really appreciate the quick and informative responses. I have always been a HUGE fan of technical forums.

---

