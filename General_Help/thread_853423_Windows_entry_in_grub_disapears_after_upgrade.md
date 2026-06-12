---
title: "Windows entry in grub disapears after upgrade"
date: 2008-07-08
forum: General Help
---

### Post by skiszkurno on 2008-07-08
Hi
Today I made upgrade of my Ubuntu, and after it I discovered that the Windows entry in the GRUB was deleted. I inserted it back with the standard commands in menu.lst:

title          Windows XP Pro
rootnotverify  (hd0,0)
makeactive
chainloader    + 1

However after rebooting of the system and trying to get to Windows I receive following information:
"Error 1: Filename must be either an absolute pathname or blocklist"

Does anybody has any idea how can I make this think start workin?

Thanks in advance

---

