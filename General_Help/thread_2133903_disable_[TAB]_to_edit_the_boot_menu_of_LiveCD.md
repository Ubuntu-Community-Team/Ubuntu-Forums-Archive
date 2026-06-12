---
title: "disable [TAB] to edit the boot menu of LiveCD"
date: 2013-04-09
forum: General Help
---

### Post by chang5562 on 2013-04-09
I created my own LiveCD based on 10.04.  However, I do not want other to re-create a LiveCD based on my by entering the boot option menu, where one can use down arrow key at booting and [tab] key to edit any of the boot option, add "only-ubiquity".  So is any way to disable the  "press [TAB] to edit option" at the bottom of the boot menu?  I have added the "menu disable" for most of the option entry, but I could not use it for all, otherwise the LiveCD won't boot, just hung there.  I also tried the timeout to 1 in isolinux.cfg.vesamenu , it only worked on faster machine such as i3, slow CPU machine still able to edit the option entry.

---

### Post by chang5562 on 2013-04-09
I found the way to boot to LiveCD directly by changing the "default vesamenu.c32" at the top of the isolinux.cfg.vesamenu to "default live", which "live" is one of the option entry - label live.  Tried with few of slow cpu boxes, it seemed fine.  press the [down] key could not get into the boot menu, LiveCD continued to boot.

---

