---
title: "strange purple screen on restart/shutdown"
date: 2006-11-07
forum: General Help
---

### Post by strabes on 2006-11-07
Whenever I restart or shutdown my computer or restart X, instead of the bootsplash, I get this wierd purple screen, but I can see some pixels of the bootsplash through it. This only happens when my computer is shutting down, not starting up. It's kinda annoying and makes linux look bad I think...

Any ideas?

---

### Post by strabes on 2006-11-07
bump

---

### Post by strabes on 2006-11-15
bump again. I waited a week. any ideas?

---

### Post by Liganic on 2006-11-18
I am having the same problem at the moment. You have installed a new kernel, with no framebuffer support or unconfigured framebuffer. I am searching for a good documentation of that in the moment.

---

### Post by strabes on 2006-11-18
Thanks. If you find a solution please post it here.

---

### Post by Solidus.s on 2006-11-26
I'm having the same problem. Also when I try the CTRL+ALT+F1. I suppouse it crash when it go from X to text mode.

---

### Post by strabes on 2006-11-26
Note: I did not have this problem on dapper.

---

### Post by junglepeanut on 2006-11-26
This is a bug, it used to be gray, many posts about it in Launchpad, recently mine turned pastel.

[http://ubuntuforums.org/showthread.php?t=305816&highlight=pastel](http://ubuntuforums.org/showthread.php?t=305816&highlight=pastel)

I posted a link to launchpad at the bottom fo that thread. Yours might be slightly different as there are many duplicates posted.

---

### Post by Liganic on 2006-11-27
Well I just had to install the framebuffer support in the kernel, adjust my grub config and voila I am seeing a testimage, so there only remains the problem to get a proper image in the proper resolution to show up.

---

### Post by junglepeanut on 2006-11-27
There are various fixes for different machines, some are listed in that link. None of them work for my system, it is the only thing I have as an issue too.

---

### Post by strabes on 2006-12-11
The way I fixed this problem was to simply remove the word "quiet" from the kernel line in /boot/grub/menu.lst 

Used to be:
> 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

Now it's:

> 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro splash vga=792
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by Liganic on 2006-12-11
Well, this just disables the splash screen completely. The real solution is to use a kernel with framebuffer enabled, the right vga= option in the grub menu.lst, quiet start activated, an initramfs Image and a reinstalled "usplash-theme-ubuntu" package :P

---

