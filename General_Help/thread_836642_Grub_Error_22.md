---
title: "Grub Error 22"
date: 2008-06-21
forum: General Help
---

### Post by neonmagnolia on 2008-06-21
I have a Vista/Gutsy dual-boot on my Dell Inspiron. I don't remember installing any upgrades or anything last night, my computer was working just fine and I didn't do anything out of the ordinary. When I turned it on this morning, however, all I got was

"GRUB Loading stage1.5

GRUB loading, please wait...
Error 22"

So how do I fix this? I'm pretty new to the linux world so any information is helpful.

---

### Post by logos34 on 2008-06-21
Boot from the ubuntu live cd and run a filesystem check:

> sudo fsck /dev/sda2 

(replace 'sda2' with whatever your ubuntu root partition is)

Then [reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by digivouk on 2008-06-24
I urgently need help with booting. I have deleted both ubuntu 7.04 partitions in windows and then tried to to a clean, new install of windows xp (I had dual boot system installed before). Now, I am receiving this grub loading 1.5 error and the computer doesn't want to boot neither live ubuntu cd nor windows cd. I am stuck here with this black screen and error.

Can someone help me out, please?

Tom

---

### Post by logos34 on 2008-06-24
> **digivouk said:**
> I urgently need help with booting. I have deleted both ubuntu 7.04 partitions in windows and then tried to to a clean, new install of windows xp (I had dual boot system installed before). Now, I am receiving this grub loading 1.5 error and the computer doesn't want to boot neither live ubuntu cd nor windows cd. I am stuck here with this black screen and error.


You're sure your Bios device boot order is set to cdrom first, then hard disk?

---

### Post by digivouk on 2008-06-24
Yes, I am sure. I have changed it to cdrom, floppy, network and then hard drive. Even tried to make a supergrub and windows boot cds and usb, however nothing worked so far. Always the same result - black screen with that error 22.

---

### Post by logos34 on 2008-06-24
> Even tried to make a supergrub and windows boot cds **and usb,** however nothing worked so far.

normally i'd say this sounds like a cdrom issue, but if even a boot usb won't work, then something else is wrong. 

There's [this page.  ]("http://users.bigpond.net.au/hermanzone/p15.htm#22")

---

