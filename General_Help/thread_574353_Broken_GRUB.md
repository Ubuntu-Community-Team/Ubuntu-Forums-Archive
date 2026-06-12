---
title: "Broken GRUB"
date: 2007-10-12
forum: General Help
---

### Post by etiennepb on 2007-10-12
Hey all,
As the title states I have a little bit of a grub issue. I decided to try Mandriva 2008 and it overwrote GRUB. Now it seems I can't boo into either(I'm posting through my live disk:cry:).  
Here is my menus.lst.
> timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,0)/boot/gfxmenu
default 0

title linux
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda1  resume=/dev/sda9 splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title linux-nonfb
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda1  resume=/dev/sda9
initrd (hd0,0)/boot/initrd.img

title 2.6.20-16-generic
kernel (hd0,0)/boot/vmlinuz-2.6.20-16-generic BOOT_IMAGE=2.6.20-16-generic root=/dev/sda1  resume=/dev/sda9 splash=silent vga=788
initrd (hd0,0)/boot/initrd-2.6.20-16-generic.img

title 2.6.20-15-generic
kernel (hd0,0)/boot/vmlinuz-2.6.20-15-generic BOOT_IMAGE=2.6.20-15-generic root=/dev/sda1  resume=/dev/sda9 splash=silent vga=788
initrd (hd0,0)/boot/initrd-2.6.20-15-generic.img

title failsafe
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda1  failsafe
initrd (hd0,0)/boot/initrd.img 
I've tried the to reindtall Grub to no avail. If anyone had any ideas...
Cheers,
Etienne

---

### Post by Pumalite on 2007-10-12
Any error message?

---

### Post by etiennepb on 2007-10-12
No error message. On power on I enter a Mandriva graphical grub menu. Selecting any one of those boots me into a bash login screen. the weird thing is, when doing the mandriva setup I was not asked the create a root account or any account for that matter??? Another strange thing is that when I edit the my menu.lst it affects the Mandriva grub screen. I at a loss.
Cheers,
Etienne

---

### Post by Pumalite on 2007-10-12
You said you tried re-installing Grub. Have you tried this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by etiennepb on 2007-10-12
I did but it was a no go.

---

### Post by Pumalite on 2007-10-12
It probably means Ubuntu is no more.

---

