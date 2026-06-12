---
title: "Wubi"
date: 2008-01-21
forum: General Help
---

### Post by valleyman7 on 2008-01-21
Is it possible to use Wubi to install Ubuntu to a USB Drive? That would be cool. :popcorn:

---

### Post by ago on 2008-01-22
yes but to make it bootable on other machines you have to install a bootloader in there (see grub4dos)

---

### Post by valleyman7 on 2008-01-22
Thanks for the quick reply. I can boot to my USB drive when booting from my Dell 9300. would this still be an option?. So if I install Wubi to my USB drive can I just select my USB drive when booting?.:)

---

### Post by ago on 2008-01-22
Yes but that is only the BIOS, it simply specifies what device to look into. But then it has to find a bootloader on that device to keep things going. You can install any bootloader capable of chainloading grub. Grub4dos is a good suggestion (since it is needed anyway).

So the steps should be: 

1) Install wubi targeting the USB device
2) Manually install grub4dos 4.3 on the USB device mbr
3) Copy over any C:\wubildr* file and C:\ubuntu\winboot\menu.lst


see the grub4dos website(s) on how to do that.

---

### Post by valleyman7 on 2008-01-22
Thanks again I thought that it was possible. :popcorn:

---

