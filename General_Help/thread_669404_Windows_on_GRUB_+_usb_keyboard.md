---
title: "Windows on GRUB + usb keyboard"
date: 2008-01-16
forum: General Help
---

### Post by selmore on 2008-01-16
Hello

I have no idea on how to dualboot Vista and Ubuntu on GRUB bootmenu. Also, on a Microsoft Comfort Curve 2000 keyboard, how would I get that working with GRUB? I have no access to BIOS either.

EDIT: The reason I have no access is because my keyboard is not reconigzed at boot.

---

### Post by wolfen69 on 2008-01-16
if you can, get ahold of a ps2 keyboard to enter bios and make sure to enable usb keyboard.

---

### Post by cloggedone on 2008-01-16
> **wolfen69 said:**
> if you can, get ahold of a ps2 keyboard to enter bios and make sure to enable usb keyboard.

Edit: Oops, wrong user. Yes I have multiple accounts but this is old.

---

### Post by _sAm_ on 2008-01-16
I had the same problem. I just bought a very cheap converter from usb to the old keyboard connector (they normally comes with all USB keyboards from Logitech and others). When using this I could enter bios, and change it to read from USB devices upon boot.

---

### Post by cdaringe on 2008-01-16
Riddle us this.
What do you have installed right currently?
If you install windows THEN install ubuntu, GRUB automatically detects the windows partition and generates its boot parameters for you (and puts it in your grub menu :) ).  This topic is pretty widely covered in the ubuntu forums if you search for 'dual boot.' however, if you already have them both installed and windows is still not there, you just need to reinstall grub.

Visit: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
Read the post by wernst
it should do it for ya.
i had the same problem with my keyboard actually. so ill try the suggestion posted above.
good luck to ya

---

