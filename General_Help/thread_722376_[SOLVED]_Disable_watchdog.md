---
title: "[SOLVED] Disable watchdog"
date: 2008-03-12
forum: General Help
---

### Post by DemonDomen on 2008-03-12
I have to disable watchdog for virtualbox, but I don't know how.

I tried adding nmi_watchdog=0 to /boot/grub/menu.lst but it didn't work.

Any ideas?

EDIT: Ok, fixed it! Here's the link to the site: [LINK]("http://forums.virtualbox.org/viewtopic.php?p=498&sid=982543f587d37a51f4f679c056b68ab2")
Looks like adding savedefault to the end fixed the thing

---

