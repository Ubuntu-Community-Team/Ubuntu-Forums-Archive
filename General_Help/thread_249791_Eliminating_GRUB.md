---
title: "Eliminating GRUB"
date: 2006-09-03
forum: General Help
---

### Post by Guybrush Threepwood on 2006-09-03
Hi,
I just installed Ubuntu and I was looking forward to getting rid of GRUB, because I want to install another OS selector, is it possible?
Thanks.

---

### Post by nstone97 on 2006-09-03
Yes it is possible.

I am using Windows XP to select which OS i want to run by editing the boot.ini file in the C drive.

What i did was installed grub to the hard drive where linux was installed in my case I did

sudu grub

root (hd1,2)
setup (hd1,2)
quit

that installs grub to hdb2 where i have linux installed

Then i used a proggie called bootpart I downloaded from the interent which will extract the boot sector from partitions and put it in my root dir of my C drive.

Then just add linux.bin (what i called the boot sector for linux) to boot.ini and thats it.

I did this because when I hybernate my PC in windows I wanted it to boot back up as it normally would before I installed linux.

---

### Post by amo-ej1 on 2006-09-03
it is possible but you still need something capable of starting linux. Things like a bootloader grub or lilo. Syslinux is popular on bootable cd's, loadlin can start linux from dos/windows, on other architectures you have milo (alpha), silo (sparc) ...

---

