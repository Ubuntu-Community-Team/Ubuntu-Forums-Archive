---
title: "How to Uninstall Ubuntu"
date: 2007-03-08
forum: General Help
---

### Post by dswhite85 on 2007-03-08
Hello

I am considering installing the latest build of Ubuntu (6.10) and I am wondering if for whatever reason Linux doesn't work out for me, will it be easy to uninstall as easy as it was to install? Also, is there any very easy to understand guides to help me learn how to uninstall all of Ubuntu successfully? Thanks in advance.

---

### Post by tribble222 on 2007-03-08
To remove Ubuntu you'll need to fix the master boot partition first.  To do that boot your windows cd, select restoration console, and type "fixmbr" then reboot when it's finished.  Then you can restore space to your windows partition by booting your ubuntu cd and running gparted.

---

### Post by pcostanza on 2007-03-12
How do you do this if you dual boot with Vista (other than reinstalling Vista)?  I've tried using the XP cd to repair and then fix mbr but it doesn't seem to work for a Vista system and the repair in Vista's boot up doesn't see any problems.
Is there another way to uninstall Ubuntu?

---

### Post by mzaiemo on 2008-02-10
hi all,
i got ubuntu install in my hd..
it sure work succesfully!!
but the problem is i want to uninstalled it..
none of the post i understand since i am really new..
help please??

---

### Post by Pumalite on 2008-02-10
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Delete Ubuntu partition. Then use your Installation CD to fix MBR
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It can also fix your Windows MBR

---

