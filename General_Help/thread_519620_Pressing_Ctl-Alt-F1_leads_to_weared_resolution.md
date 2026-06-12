---
title: "Pressing Ctl-Alt-F1 leads to weared resolution"
date: 2007-08-07
forum: General Help
---

### Post by varun_shrivastava on 2007-08-07
hi 
i want to know whether i can change the resolution of the screen
when in console mode.

When i enter console mode, the font size is too big, which makes it difficult to read.

kindly suggest some solution

thanks
varun

My OS is Ubuntu Feisty 7.04

---

### Post by kerry_s on 2007-08-07
add> vga=791 <to your /boot/grub/menu.lst

sudo gedit /boot/grub/menu.lst

example:
kernel          /boot/vmlinuz-2.6.18-4-686 root=/dev/hda2 ro vga=791

---

### Post by varun_shrivastava on 2007-08-07
thanks it worked

---

