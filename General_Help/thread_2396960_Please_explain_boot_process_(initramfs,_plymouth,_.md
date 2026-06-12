---
title: "Please explain boot process (initramfs, plymouth, lightdm)"
date: 2018-07-23
forum: General Help
---

### Post by Nyyr on 2018-07-23
Hello,

I have full disk encryption except /boot volume. During boot plymouth displays password prompt, but NumLock key does not work. I found that this can be solved via
lightdm configuration file specifying numlockx to be run and although NumLock LED is not lit, numeric pad keys work as numbers. OK.

What I cannot understand is this: Because the disk is fully encrypted, there is no numlockx or lightdm available until I enter password in the plymouth password field, except if it was placed inside initramfs. But when I list content of the initramfs, there is no numlock, no lightdm. WTF? How does it work then? Xubuntu 18.04.

---

### Post by VMC on 2018-07-23
Settings Editor > Keyboards > Numlock

---

