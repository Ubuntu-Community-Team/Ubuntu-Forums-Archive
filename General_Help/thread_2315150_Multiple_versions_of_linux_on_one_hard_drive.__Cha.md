---
title: "Multiple versions of linux on one hard drive.  Change which comes up automatically?"
date: 2016-02-26
forum: General Help
---

### Post by Tom_Carr on 2016-02-26
I have a computer with 3 distros of linux installed on the hard drive (2 ubuntu and 1 kubuntu).  When I turn it on a menu comes up that lets me select which version I want to use, but if I do nothing the most recent version always is used.  Is there any way to change this so that an older version comes up automatically?

---

### Post by newbie-user on 2016-02-26
Editing the GRUB settings will allow you to change which version boots automatically. See here: [http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/]("http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/")

---

### Post by QDR06VV9 on 2016-02-26
There is a couple of ways to do this..
> Grub Customizer is a graphical interface to configure the GRUB2/BURG settings and menuentries

Features:
 * move, remove or rename menuentries (they stey updatable by update-grub)
 * edit the contents of menuentries or create new ones (internally it edits the 40_custom)
 * support for GRUB2 and BURG
 * reinstallation of the bootloader to MBR
 * settings like default operating system, kernel params, background image and text colors etc.
 * changing the installed operating system by running on a live cd
The PPA is here: [https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)
Or you can carefully edit Grub by hand outlined here:  [http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)
Hope this is helpful..

---

### Post by yancek on 2016-02-26
When you install the default for the Grub bootloader is to install to the MBR which most people do and that is why the last install is always first.  Boot the last system installed and open the file /etc/default/grub using sudo with whatever text editor you have.  Example:   sudo gedit /etc/default/grub   Change the line below at the top of the file:

```
GRUB_DEFAULT=0
```

Change the zero to whichever number you want.  If the menuentry you want is the third in your Grub boot menu, replace the 0 with 2 as Grub counts from zero.  Save the file and run sudo update-grub and reboot.

---

### Post by Dennis N on 2016-02-26
You can choose your own list order and create your own names for each OS if you learn how to create custom grub menu entries. The advantages of this are explained in the article:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

The section "Maintainance-Free Menuentries" explains how to make them so that they never need updating. This is a most attractive feature for someone who multiboots several operating systems.

---

