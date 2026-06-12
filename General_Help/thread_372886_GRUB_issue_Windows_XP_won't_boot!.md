---
title: "GRUB issue: Windows XP won't boot!"
date: 2007-02-28
forum: General Help
---

### Post by communistirishjew on 2007-02-28
I've had Dapper and XP dual-booted on my computer for a while, and yesterday it just randomly decided that it would not allow Windows to boot up. My computer hangs at the following message:

[B]Booting 'Windows XP'
root (hd0,0)
Filesystem type is fat, Partition type 0xc
savedefault
makeactive
chainloader +1[/B]

The entry in my grub file [/boot/grub/menu.1st] is:

[B]title		Windows XP
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader +1[/B]

I've tried getting rid of the **savedefault** line, as well as to change **root** to **rootnoverify**, but to no avail. Please help.

---

