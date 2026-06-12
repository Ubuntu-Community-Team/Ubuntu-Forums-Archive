---
title: "removing Ununtu"
date: 2007-08-05
forum: General Help
---

### Post by rules on 2007-08-05
Hi guys

I have been playing with Ubuntu for a while now on my Xp machine (laptop) but I have decided to change back to Suse. My problem is that since installing Ubuntu it does not allow my Suse cd to boot up anymore. Any ideas of what I can do?

Thanks.

---

### Post by logos34 on 2007-08-05
are you sure the cdrom is set first in the bios device boot order?  I doubt it's anything to do with ubuntu. And why go back to Suse?  I liked suse once upon a time but ubuntu  is much better.

---

### Post by rules on 2007-08-05
Yes I'm sure. When I put the Ubuntu cd in it boots up to Ubuntu, but when trying to boot with my Suse 10.2 cd, which I have used before, it just loads to windows.

My biggest gripe with Ubuntu is that every time I booted up I had to battle to get the wireless card to work and it seems as if they made it so user friendly that in some instances they sort of tie your hands. Suse I load my wireless card once and it keeps working, its a bit more tricky to use but you get use to it.

Cheers.

---

### Post by Tomosaur on 2007-08-05
It sounds like it's the Suse CD which is the problem to be honest. Grub shouldn't load at all if a bootable CD is in the drive, and if it skips Grub and goes straight to Windows, then something is very wrong indeed. Best advice is to re-check the CD and make sure its ok.

As for removing Ubuntu, all you need to do is:

a) Make sure you have a working bootloader, then
b) Format the Ubuntu partitions using whichever partition manager you prefer. You could even use the Ubuntu LiveCD to remove Ubuntu.

---

