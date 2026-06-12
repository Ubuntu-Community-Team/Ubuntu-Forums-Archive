---
title: "Dual Boot in Vista Bootloader Question!"
date: 2007-05-08
forum: General Help
---

### Post by Scubastev013 on 2007-05-08
I have a Dell Inspiron E1505 with Windows Home Premium Preinstalled.  I would like to install 7.04 and dual boot the machine.  The only thing is, I would like to use the windows bootloader.  I'm more comforatable with the windows loader, and if the computer ever needs servicing, it will be easier on them.  The goal is to have vista boot automatically, unless i catch it with F12 or whatever it is.  I installed 7.04 on my XP machine, but was not sucessful in getting xp to boot first without me having to catch it.  I would the exact code for what I need to change or whatever.


Thanks,

Scuba

---

### Post by ohgod on 2007-05-08
I'm not 100% sure, but I don't think this is possible.  I haven't used Vista, but I know that previous m$ bootloaders don't play nicely with other non m$ operating systems.  

For example, if you installed Ubuntu first, then XP,  XP would overwrite grub and you wouldn't be able to boot Ubuntu without a rescue disk.  I imagine the same thing would happen with Vista.

So I'd recommend just sticking with Ubuntu's bootloader, grub.  You can easily set your Vista partition to be the default boot option if you want (by editing /boot/grub/menu.lst).

---

