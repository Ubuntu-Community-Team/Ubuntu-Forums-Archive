---
title: "Problem loading windows from grub"
date: 2007-03-04
forum: General Help
---

### Post by medeshago on 2007-03-04
By mistake i installed grub in the windows partition. I did: sudo grub-install /dev/sda1 (the windows partition). And now i can't acces the windows partition through ubuntu.
It can't be mounted:
medeshago@medeshago:~$ sudo mount -a
Unexpected clusters per mft record (-1).
Failed to startup volume: Argumento inválido
Failed to mount '/dev/sda1': Argumento inválido
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
And worse, when i try to enter Windows through Grub all i get it's Grub written all across the screen. 
I tried reinstalling grub, and that didn't work. I'm a noob so help me.

---

### Post by medeshago on 2007-03-04
i really really need help!

---

