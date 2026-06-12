---
title: "windows xp not on grub screen"
date: 2007-07-10
forum: General Help
---

### Post by richmellis on 2007-07-10
hello, I was trying to fix a problem with my desktop effects "the composite extension is not available", but when I rebooted, I noticed that windows xp disappeared from the grub bootloader screen.  I went into gParted and I got this message (hopefully the screenshot is attached):

Warning: unable to read the contents of this filesystem!  Because of this some operations may be unavailable.  Did you install the correct plugin for this filesystem?

Any ideas on how to be able to get back into windows? 
thanks, Rich.

---

### Post by hooksie on 2007-07-10
What did you do to try to fix the desktop effects?

I can't be sure, but maybe

> sudo update-grub

will work.

---

### Post by richmellis on 2007-07-10
I'll try to attach the original page that I was working on, but I was also working from this link:
Re: 3d effects cube not working with ATI
I had the same problem you did. You have to install the fglrx driver for your graphics card:
[http://www.howforge.com/how-to-setup...-ubuntu-feisty](http://www.howforge.com/how-to-setup...-ubuntu-feisty)

after I entered "sudo update-grub, I got the following:

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

however, xp is not listed.

thanks

---

### Post by richmellis on 2007-07-10
Hi I was able to fix it by going to the terminal and entering:

sudo gedit /boot/grub/menu.lst

which loads the GRUB menu file (which is basically a text file) within GEdit.  I then scrolled to the bottom of the file and entered:

title                      windows XP
root                     (hd0,1)
makeactive
chainloader       +1

then I saved the file and rebooted and Windows xp was back on the list.

---

