---
title: "Grub Help!! Cant find ubuntu install"
date: 2007-09-20
forum: General Help
---

### Post by haley183 on 2007-09-20
I am ready to give up on ubuntu! I installed vista one one hd and then feisty on another hd and everything worked perfect. i set up feisty like i wanted and everything was great. then i decided i didnt want vista anymore and installed xp pro on the first hd. of course this wiped the grub loader. i tried everything to install grub back right to get back to using ubuntu again. nothing worked, not even the super grub disk. so i finally gave up and reinstalled ubuntu thinking that it would reinstall grub and everything would fall into place. HA! 

i kept getting error 17. so i used super grub disk to fix it. now grub loads and brings up the option to pick ubuntu or windows. the problem is that when i pick ubuntu, it cant find it! i pick xp and it loads perfectly fine. no matter what i try, it still cant find ubuntu.

i booted to the live cd again to check the /boot/grub/menu.lst file to see if something was wrong with it, but when i open it, its empty! ive tried reading all kinds of forums and tried every command people speak of. i dont know what to do anymore! help!

---

### Post by dcstar on 2007-09-20
> **haley183 said:**
> 
..........
i booted to the live cd again to check the /boot/grub/menu.lst file to see if something was wrong with it, but when i open it, its empty! ive tried reading all kinds of forums and tried every command people speak of. i dont know what to do anymore! help!

That file is part of the "live" CD, and not you hard disk.

You have to boot off the live CD, install the **gparted** package and then use that tool to identify your Ubuntu install and then manually mount that filesystem.

You can then find the menu.lst file on that drive - but I'm not sure that will do much good if you have the error 17 issue.

Gparted will at least tell you the /dev/hd or /dev/sd designation of your Ubuntu partition, then you may be able use that in your Super Grub disk to fix things.

---

### Post by dresman on 2007-09-20
windows hates linux:popcorn:

---

### Post by haley183 on 2007-09-20
okay. well how to you install the gparted package?

---

### Post by g2g591 on 2007-09-20
"sudo apt-get install gparted" (in the terminal) just remember that if you install it on the livecd, once you reboot you must reinstall it

---

