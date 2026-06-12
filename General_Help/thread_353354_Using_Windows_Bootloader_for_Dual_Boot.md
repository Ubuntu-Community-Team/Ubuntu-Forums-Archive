---
title: "Using Windows Bootloader for Dual Boot"
date: 2007-02-04
forum: General Help
---

### Post by CocoAUS on 2007-02-04
My sister needs Windows so she can play Guild Wars, but she's really loving my Ubuntu install.  So when we tried putting both Windows and Ubuntu on her drive, her gaming keyboard would not work to select the options in GRUB (though it works fine in Ubuntu).

Anyway, the question is this:

How would I go about setting up the dual boot to use the Windows bootloader?

---

### Post by tchoklat on 2007-02-05
If she has a USB keyboard it will not function to use GRUB. I have two K/Bs connected to overcome this as I use the Linux GRUB.

---

### Post by reclusivemonkey on 2007-02-05
> **tchoklat said:**
> If she has a USB keyboard it will not function to use GRUB. I have two K/Bs connected to overcome this as I use the Linux GRUB.

It will, you just need to alter the BIOS settings. I will post what you want to look for when I get home from work.

---

### Post by reclusivemonkey on 2007-02-05
OK, go into your BIOS. In mine, the section called "Advanced Chipset Features" is where I do this. Find "USB Keyboard Support" and make sure its enabled. Save, reboot and your USB keyboard should work in GRUB.

---

