---
title: "Can access GRUB menu"
date: 2007-01-10
forum: General Help
---

### Post by facugaich on 2007-01-10
Hi, I installed Ubuntu Dapper to dual boot with Win XP and then configured GRUB to default to XP with a timeout of 0.

The problem is I can't access the menu to select which OS to boot. I read you have to press ESC during boot, but this doesn't seem to work for me. Sometimes I can see a menu flash but then it disappears and XP boots... any ideas?

---

### Post by bodhi.zazen on 2007-01-10
LOL facugaich

Boot the live CD, mount the ubuntu partition, edit /boot/grub/menu.lst from there 8)

I assume you can do, if not re-post and I will assist further :)

---

### Post by facugaich on 2007-01-10
I mispelled the title it's suppossed to be "Can't..."

I know, I can access the menu.lst file... but what I want is to be able to default to win xp (cause my mom uses this PC) and when I want to boot ubuntu I press ESC to get to the menu... But it's not working.

When I had breezy I would install grub in a floppy rather than the MBR, but this option comes no longer with Dapper's install CD (The one from ShipIt). It is only avaliable with the alternative install CD which is only for download.

---

### Post by bodhi.zazen on 2007-01-10
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)

---

