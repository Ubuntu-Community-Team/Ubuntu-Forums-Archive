---
title: "Cannot see booting info"
date: 2008-01-10
forum: General Help
---

### Post by austin183 on 2008-01-10
Hello all,

I am running Ubuntu 7.10.  When my system boots up, it shows a few lines of the boot process, and then it goes to a blank screen for a couple of minutes before it comes up to the login screen.

It is unnerving.  I would like to see the boot processes, but I can't figure out how to do it.

I think I need to edit the /boot/grub/menu.lst file. Here is my current boot item:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=#######(blah) ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

What do the "ro" and "splash" switches do?  No matter how I word my search in Google, it won't give me any useful information.

Thanks!

---

### Post by wolfen69 on 2008-01-10
the word "quiet" refers to not being able to see what's happening during bootup.

---

