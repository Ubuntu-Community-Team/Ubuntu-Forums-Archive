---
title: "Kernel Upgrade"
date: 2005-04-10
forum: General Help
---

### Post by SolidStClair on 2005-04-10
How do I go about upgrading my Kernel to the latest 2.6.11.7 release in Hoary? Once I do, do I have to customize it in any way?

---

### Post by XDevHald on 2005-04-10
Just a tip for the new kernel, as I have experienced it is bugged in a huge way to where it will stop all processes in loading when you login and only load the top taskbar and will only show the brown background, now I am not sure if this has happened to anyone else on the board, but it will hang and freeze your HD.

Just another tip, CTRL + ALT + Delete will not work as well with CTRL + ALT and Backspace, which this is normally used to log out.

My recommendation is to sit with the latest kernel and image of 2.6.10-5 386 or i686 until this has been fixed.

---

### Post by az on 2005-04-10
Those kernels are unsupported - they are in universe.

When you install a linux-image, you are getting a precompiled distribution kernel.  Since they are precompiled, you do not have to configure anythig.  Sice linux-image packages are installed by the packagemanagement system, everything (initrd, grub bootloader) is set up for you to ensure that you are not left in an unbootable state.

This means that you can always boot back into your old kernel if the new one no worky.

The 2.6.10 kerneles in Hoary are going to receive bug fixes ans security patches, not the 2.6.11 ones.

You can also use the Warty kernel which is just fine.

---

### Post by sinbad782 on 2005-04-10
I tried 2.6.11 the other day on an install of Debian Unstable and it appeared to be highly buggy. One major problem was typing from an AT type keyboard - a load of gobbledegook kept being output, with multiple characters for each keypress.

Wouldn't recommend it!

---

### Post by jeremy on 2005-04-10
I had exactly the same problem as Doc with 2.6.11

---

### Post by SWAT on 2005-08-26
[QUOTE=BB]Just a tip for the new kernel, as I have experienced it is bugged in a huge way to where it will stop all processes in loading when you login and only load the top taskbar and will only show the brown background, now I am not sure if this has happened to anyone else on the board, but it will hang and freeze your HD.

Just another tip, CTRL + ALT + Delete will not work as well with CTRL + ALT and Backspace, which this is normally used to log out.

My recommendation is to sit with the latest kernel and image of 2.6.10-5 386 or i686 until this has been fixed.[/QUOTE]

I also had exactly the same experience. It's a pity though

---

