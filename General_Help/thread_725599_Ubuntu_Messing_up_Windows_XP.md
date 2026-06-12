---
title: "Ubuntu Messing up Windows XP"
date: 2008-03-15
forum: General Help
---

### Post by AdHavoc on 2008-03-15
I recently installed Gutsy Gibbon 7.10 on a dual boot setup (with Windows XP), and everything went perfectly on the Ubuntu side.  However, when I boot into my Windows installation, the screen is about 1/3" off to the right and even doing the Auto-Adjust barely helps (if at all).  The manual configuration for changing the screen positions is not exact enough and I end up with the screen 1/3" inch away in a different direction.  I think before my resolution was 1024 x 800 and now it is showing up as 1024 x 768.  Is there any way I can change this?

---

### Post by gobbles414 on 2008-03-15
> **AdHavoc said:**
> I recently installed Gutsy Gibbon 7.10 on a dual boot setup (with Windows XP), and everything went perfectly on the Ubuntu side.  However, when I boot into my Windows installation, the screen is about 1/3" off to the right and even doing the Auto-Adjust barely helps (if at all).  The manual configuration for changing the screen positions is not exact enough and I end up with the screen 1/3" inch away in a different direction.  I think before my resolution was 1024 x 800 and now it is showing up as 1024 x 768.  Is there any way I can change this?

Obviously, make sure that you're using the same resolution in Ubuntu as in XP. That way, your monitor won't have to switch resolutions for each operating system. Just in case you don't know how to manage your resolution in Ubuntu, it's *System => Administration => Screens and Graphics*. Alternatively, you can go *System => Preferences => Screen Resolution*.

Does this help?

---

### Post by chazn85 on 2008-03-15
are you using a laptop by any chance?

I had the same issue with mine but was resolved by editing the xorg.conf

---

### Post by gobbles414 on 2008-03-15
> **chazn85 said:**
> are you using a laptop by any chance?

I had the same issue with mine but was resolved by editing the xorg.conf

For those new to Linux, the easiest way to edit xorg.conf is the following:

1. Do you get a GRUB menu as your computer boots asking if you want Ubuntu or XP? If not, press the escape key on your keyboard as your computer is booting. Otherwise, allow your computer to start booting normally.
2. In GRUB, choose the *Rescue Mode* for your highest kernel version.
3. You computer will boot to a command line interface. Type *sudo dpkg-reconfigure xserver-xorg* and press enter on your keyboard.
4. Follow the instructions in the wizard. When you're done, type *sudo reboot* and then press enter. Boot normally and log into Ubuntu.

---

