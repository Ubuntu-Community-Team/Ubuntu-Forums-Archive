---
title: "Two Grubs -- are there two menu.lst?"
date: 2008-02-21
forum: General Help
---

### Post by HHelsinger on 2008-02-21
I have XP on one drive,and Gutsy on a partition on a second drive.  In order to get  Gutsy to boot properly on the second drive , I had to edit the /boot/grub/menu.lst to remap (hd0) > (hd1) and vice versa.   that menu.lst is on the second drive (hd1).  (When I boot directly from the Gutsy partition of (hd1), the system thinks it is (hd0).  that is why I had to remap the drives in the menu.lst).   

When I tried to install Grub on Drive 1 (hd0)  using Super Grub Disk, I wound up with the same /boot/grub/menu.lst there too.   If it is to work properly, I need to edit  Grub on drive one (hd0), to remove the remapping of the two drives.   I can do it when the Grub menu comes up while booting --   

How do I make permanent the changes which I enter while booting?  

Editing /boot/grub/menu.lst from inside Gutsy on drive 2 (hd1) will, I think, only alter what happens when I boot from that drive, but I don't think it will alter the Grub menu that appears when I boot on drive 1(hd0).   Or is the same /boot/grub/menu.lst referred to in both cases?

---

### Post by logos34 on 2008-02-21
> **HHelsinger said:**
> Or is the same /boot/grub/menu.lst referred to in both cases?

Yes.  You installed grub stage1 to the mbr of both drives, but they both refer to the same menu.lst in /boot/grub on the linux root partition.

If you want the XP drive first in the boot order, then grub should go there, but should point to (hd**1**,x)--i.e. menu.lst on the second drive.

Set the XP hard disk as the boot drive in the Bios.  Then boot into ubuntu, using either the super grub disk or manually like you've been doing, and make the changes permanent by editing menu.lst as root:

**gksudo gedit /boot/grub/menu.lst**

change the 'groot' and 'root' lines to (hd1,x)

Rewrite grub to the mbr of the XP drive:

> **sudo grub**

> **find /boot/grub/stage1**
(should output 'hd1,x'--enter this in next command)
> **root (hd1,x)**
> **setup (hd0)** (--> this will write it to the xp disk, but pointing to ubuntu root)
>** quit**

You can also use SGD to 'uninstall' grub from the mbr of the ubuntu drive

---

### Post by HHelsinger on 2008-02-21
Thanks.   This is far more elegant than the solution I devised, which was to have a double  set of menus in menu.lst -- one set to be used when booting normally from the XP drive,  and a second set to be used when booting from the ubuntu drive after I get into the boot menu by hitting F12.

My double menu works, but you are right -- now that the grub menu on the XP drive works to boot ubuntu on the 2nd drive, there is no reason to keep grub on the mbr of the ubuntu drive, and once I remove it I can go back to a simpler and shorter grub menu.

thanks again

---

