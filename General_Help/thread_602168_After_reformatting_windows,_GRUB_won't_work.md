---
title: "After reformatting windows, GRUB won't work"
date: 2007-11-04
forum: General Help
---

### Post by melzmirth on 2007-11-04
I have two hard disks: one for Windows and another one for Ubuntu.

Recently ,my Windows was refomatted. I'm quite sure my Ubuntu is still intact.

The GRUB isn't working anymore. I can't fix it with my live CD because it's not working too. When I boot from the live CD, it  kept saying it can't open the GNOME and once it enters Ubuntu's desktop, the icon for installation won't run.

Am I doomed?

---

### Post by minus198 on 2007-11-04
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

That seems like an easy guide. Good luck :)

---

### Post by froy02 on 2007-11-04
Snce you installed ubuntu on a second drive it should still be intact. Re-install windows on the reformatted drive. Now you have a working OS.

or go your friend's computer and download Super grub.

Now you have a working OS.

Go to this site
 [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) 
and grab a copy of super grub.  Follow the instructions and you should recover your setup. 

NOTE:  If ubuntu is installed on a 2nd drive you can NOT reformat the first drive because you lose the grub boot instructions which are ALWAYS written on the first hard drive's  MBR.  When you format the MBR is over-writen by the format utility.

Also you can not switch hard drives like making the master to slave after the installation.

---

### Post by melzmirth on 2007-11-04
Minus, thank you for the help. That was a very clear guide compared to those that I have read before. Thanks!

---

