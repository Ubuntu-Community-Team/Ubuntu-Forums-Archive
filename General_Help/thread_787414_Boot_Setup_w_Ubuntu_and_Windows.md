---
title: "Boot Setup w/ Ubuntu and Windows"
date: 2008-05-08
forum: General Help
---

### Post by bielers on 2008-05-08
Hi!

I have my Ubuntu installed in my external hard drive, so that wherever I go, I could bring my external hard drive with me.

However, what happens is that when I take out of the external drive, and open my PC, it does not allow me to open my Windows. I have to plug it in, and select on the boot menu.

How could I resolve this, so that I could boot the Windows on my PC without the external hard drive.

Thank you =)

---

### Post by confused57 on 2008-05-08
First you need to restore Window's IPL(Initial Program Loader) to the internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You can use a Windows install cd(not a recovery disk) or Super Grub Disk.

Then you need to install grub's IPL to the external hard drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Which would be something like:
```
root (hd1,0)
setup (hd1)
```

Boot first to your external drive, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it already is.  This is temporary, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```
Change the line with #groot to (hd0,x).

---

### Post by bielers on 2008-05-08
Thanks for the info, confused57

However, I am confused with the first step.

I am trying to download the Super Grub Disk, and it says that it only takes 400KB. What should I pick? Is it the ISO, not the EXE file?

---

### Post by confused57 on 2008-05-09
You'll need to download the iso, burn it as an image(not as a data or bootable cd) and at a low speed(8x or less).

---

