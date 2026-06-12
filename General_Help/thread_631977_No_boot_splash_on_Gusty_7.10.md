---
title: "No boot splash on Gusty 7.10"
date: 2007-12-05
forum: General Help
---

### Post by darkstr2o4 on 2007-12-05
I just upgraded to Gusty 7.10 and there doesn't seem to be any default boot splash.  The screen just stays black until the login screen is reached. Any help on this would be greatly appreciated.

---

### Post by logos34 on 2007-12-05
there should be a 'splash' at the end of kernel line in /boot/grub/menu.lst.

Or try [this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen") or[ this]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown").

---

### Post by darkstr2o4 on 2007-12-05
well I had to make some changes to control my mouse but even the first time I booted up it was not there

---

### Post by darkstr2o4 on 2007-12-05
Okay, I had to append the kernel commands in /boot/grub/menu.lst so the mouse on my thinkpad stopped going crazy. so now the ending has changed, however it is still there.  It now reads:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a1822164-88b6-4478-b7e0-3cd51de249bb ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.22-14-generic
quiet

Should this be working correctly? Will these other methods of fixing this problem affect the correction needed for the mouse to stay under control?

---

### Post by logos34 on 2007-12-05
not sure...you could try the second fix first (at least you don't have to add anything to the kernel line for that)

---

### Post by darkstr2o4 on 2007-12-05
got it thanks for the help

:)

---

