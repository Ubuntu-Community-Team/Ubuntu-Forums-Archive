---
title: "I have a Debian Themed bootloader?"
date: 2013-01-10
forum: General Help
---

### Post by athletesrun on 2013-01-10
This isn't really a problem or anything, but when I boot my pc and it's asking me what OS to start, the GRUB 2 bootloader is Debian themed.  It shows the Debian logo and has a bunch of Debian themed decoration all around the screen.  I run Ubuntu 12.04.  Is this a bug or are all the ubuntu bootloaders like this?

---

### Post by Frogs Hair on 2013-01-10
> I boot my pc and it's asking me what OS to start, the GRUB 2 bootloader is Debian themed. 

Is this a dual boot with Debian or another operating system ? The screen should appear something like the shot below. I know grub can be customized, but you would know if you had done that if you are the only user.

---

### Post by vasa1 on 2013-01-10
> **athletesrun said:**
> This isn't really a problem or anything, but when I boot my pc and it's asking me what OS to start, the GRUB 2 bootloader is Debian themed.  It shows the Debian logo and has a bunch of Debian themed decoration all around the screen.  I run Ubuntu 12.04.  Is this a bug or are all the ubuntu bootloaders like this?

Have you installed the Xubuntu desktop? I got a Debian look after that.

---

### Post by stinkeye on 2013-01-10
Have a look in /boot/grub for a a debian pic.
Probably placed there by xubuntu.
Grub automatically looks for a background pic in /boot/grub and uses it if one exists.
Try removing and see what happens.

---

### Post by athletesrun on 2013-01-11
> **Frogs Hair said:**
> Is this a dual boot with Debian or another operating system ? The screen should appear something like the shot below. I know grub can be customized, but you would know if you had done that if you are the only user.

No, I only Dual-boot Windows XP and Ubuntu.

---

### Post by athletesrun on 2013-01-11
> **athletesrun said:**
> No, I only Dual-boot Windows XP and Ubuntu.

I found the pics for the theme in \boot/extlinux/themes/debian.  Is it okay to delete them?

---

### Post by MadmanRB on 2013-01-11
> **athletesrun said:**
> I found the pics for the theme in \boot/extlinux/themes/debian.  Is it okay to delete them?


No I wouldnt mess with it as grub is very sensitive.
I had this happen to me usually when using certain package combos like xubuntu desktop.
But its honestly nothing to worry about, Ubuntu is based on debian and the branding usually comes from upstream packages.
To be honest I almost like the debian themed grub more then the default ubuntu one, looks a bit more fancy.

---

### Post by athletesrun on 2013-01-11
Okay, Thanks for all your help!

---

