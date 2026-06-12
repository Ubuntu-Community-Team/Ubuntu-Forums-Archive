---
title: "Boot-Repair not working."
date: 2013-10-24
forum: General Help
---

### Post by ddawsonn on 2013-10-24
I'm having problems access my 13.04 installation. It's installed on a 120GB drive in my laptop and was working fine until today when I installed OS X on a 2nd hard drive in my laptop and now I cannot boot into the ubuntu installation. I've ran boot-repair from a LiveUSB but it hasn't fixed the problem. Would someone be able to look at this, [http://paste.ubuntu.com/6297745](http://paste.ubuntu.com/6297745) and identify the problem as I'm quite new to all this and can't make a lot of sense from it.

Thanks for any help.

---

### Post by Impavidus on 2013-10-25
I think that your computer boots from the second hard drive, which only boots OS X. The boot loader on the first hard drive, grub, knows about both Ubuntu and Mac OS X and should give you a menu where you can choose your OS. Maybe you have to modify the boot order in the bios.

---

