---
title: "Windows XP option missing from Grub after upgrade"
date: 2008-06-25
forum: General Help
---

### Post by chrisgeller on 2008-06-25
Hi

I have Hardy Heron, and performed an upgrade during which my laptop ran out of power (oops). When I turned on the laptop, only Ubuntu was present on Grub. I've been able to complete the upgrade (I had to dpkg --configure -a to do it), but Windows is still not present in Grub.

Any ideas how to get it back?

---

### Post by geo909 on 2008-06-25
Check your grub configuration file:
```
gedit /boot/grub/menu.lst
```
Can you find any entry for windows?

If you don't, I guess you should add the appropriate lines.
Unfortunately I'm on a live cd now and I don't know which lines.

---

### Post by logos34 on 2008-06-25
here you go:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

---

