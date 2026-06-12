---
title: "Win XP option in GRUB disappered"
date: 2007-05-10
forum: General Help
---

### Post by tnic on 2007-05-10
I have Ubuntu 6.xx / Win XP installed on my laptop with GRUB boot loader. When I did some updates via update manager and rebooted, the option "Windows XP" in grub was replaced with "Ubuntu 2.17.x- ..". 

Is there an easy way out of this mess, I am sadly highly depended of Win XP.

Thanks!

---

### Post by kragen on 2007-05-10
If you look in /boot/grub look a file called "menu.lst" The file named "menu.lst" specifies the entries in the grub menu - if you add the following to the bottom of the file, you should end up with an extra entry which boots windows XP.

```
title       Windows Xp
root        (hd0,0)
makeactive
chainloader +1
```

You may need to tweak the line "root (hd0,0)" to point to your windows partition - the first number (the hd0 bit) refers to the drive and the second number refers to the partition number (starting at 0) - so if your windows partition is the second partition on your first hard drive, you need to use "(hd0,1)".

The easiest way to find this out will be to look in the /boot/grub directory for some sort of backup - if you're lucky the updater should have made one - just look in there and compare.

---

### Post by tnic on 2007-05-10
Thanks a lot! 

It was not that difficult, I guess I had some sort of panic attack O:)

---

