---
title: "cannot log into Ubuntu"
date: 2008-02-02
forum: General Help
---

### Post by 123my on 2008-02-02
My computer has 2 hard disk, master is for Windows XP and slave is for Fedora 6 (first partition) and Ubuntu 7.10 (second partition). Every time when I start my computer, boot loader of ubuntu come out and let choose the OS. After I install Fedora 8, the formet boot loader is replaced by Fedora boot loader and I cann't log into Ubuntu. What should I do?

---

### Post by SpiderGorilla on 2008-02-02
Uhm, going to sound heartless, but have you checked the Fedora forums yet? You probably need to edit their boot-loader to allow Ubuntu to show up.

---

### Post by jeffus_il on 2008-02-02
> **123my said:**
> My computer has 2 hard disk, master is for Windows XP and slave is for Fedora 6 (first partition) and Ubuntu 7.10 (second partition). Every time when I start my computer, boot loader of ubuntu come out and let choose the OS. After I install Fedora 8, the formet boot loader is replaced by Fedora boot loader and I cann't log into Ubuntu. What should I do?
Boot Fedora and post your ```
/boot/grub/menu.lst 
```
Also in a terminal run:
```
sudo parted /dev/sda print
```

replace sda above with your Fedora/Ubuntu disk
and post the output

---

