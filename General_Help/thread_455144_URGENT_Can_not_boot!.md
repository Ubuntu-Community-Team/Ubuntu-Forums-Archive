---
title: "URGENT: Can not boot!"
date: 2007-05-26
forum: General Help
---

### Post by loathsome on 2007-05-26
Hi,

I tried out this "StartUp-Manager (SUM)", because I wanted to change my usplash screen. I did nothing more than change it from the Kubuntu one to the Xubuntu one. Now my laptop wont boot.

It gets to the part right before the splash screens shows up ("Loading..."), and the it stays like that for ever. I have the LiveCD, so if there's a way to restore the bootfiles (copy from the livecd etc) **please** let me know.

Thanks a lot!

---

### Post by nemarasu on 2007-05-26
what does your /etc/grub/menu.lst look like?

have you tried booting into recovery mode?

---

### Post by loathsome on 2007-05-26
Yes, I tried the recovery mode.

I'll post the "menu.lst" later on, I'm currently in WXP! ._.

Though, I don't think this actually has got anything to do with GRUB, because .. GRUB works fine, and as far as I know, usplash got nothing to do with GRUB.

Thanks for your reply.

---

### Post by loathsome on 2007-05-26
Bah, nvm then :-P

.. there goes reinstall #45920.

---

### Post by Jimmy_r on 2007-06-01
It was probably caused by the update-initramfs command.

If you encounter this problem again, try to edit the boot entry(press e at grub menu) and add .bak at the end of the initramfs path.

---

### Post by loathsome on 2007-06-01
> **Jimmy_r said:**
> It was probably caused by the update-initramfs command.

If you encounter this problem again, try to edit the boot entry(press e at grub menu) and add .bak at the end of the initramfs path.

Yeah, but .. I don't think I'll use SuM in a while anyway;)

---

### Post by Jimmy_r on 2007-06-05
Well, update-initramfs is run at system upgrades too...

---

