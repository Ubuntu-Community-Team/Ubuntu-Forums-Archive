---
title: "[SOLVED] Hardy 8.04,Grub Start, Error 11: Unrecognized device string"
date: 2008-05-05
forum: General Help
---

### Post by hosammy on 2008-05-05
After upgrade from Hardy Beta to formal release 8.04,
From Grub Manager, Press to start, then appear:
Error 11: Unrecognized device string
   Press Any key to continue ....

Then I press any key to return to the grub manager again.

Then I select the Recovery Kernel
It runs for almost 2 pages of commands and appears a screen, then I select:
resume :   resume normal boot

Then everything is OK.

Please advise ....

:confused:

---

### Post by amohanty on 2008-05-06
Can you post your /boot/grub/menu.lst

AM

---

### Post by hosammy on 2008-05-06
> **amohanty said:**
> Can you post your /boot/grub/menu.lst

AM

/boot/grub/menu.lst

default 0
timeout 600

title Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root 
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3588b677-8237-41ac-8ca4-c016e775ea40 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
#quiet
savedefault

title Ubuntu hardy (development branch), kernel 2.6.24-16-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3588b677-8237-41ac-8ca4-c016e775ea40 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu hardy (development branch), memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Home Edition
root (hd0,0)
chainloader +1
savedefault

---

### Post by amohanty on 2008-05-06
The fourth line that just says **root**, change that to look like the others i.e. **root (hd1,0)**

AM

---

### Post by hosammy on 2008-05-07
> **amohanty said:**
> The fourth line that just says **root**, change that to look like the others i.e. **root (hd1,0)**

AM

After changing the fourth line as root (hd1,0)
the problem fixed.
Thank you very much.
:lolflag::guitar:

---

