---
title: "Ubuntu doesn't boot in a normal way"
date: 2007-12-25
forum: General Help
---

### Post by Ferux on 2007-12-25
Every time I try to boot Ubuntu in the 'normal' way (switching on my pc and waiting), the Ubuntu logo shows up, but the orange bar stops at the very first point. When I select the recovery mode, I don't receive any errors. I don't like that recovery mode since only the root can log in. Starting X (with 'startx') works, but the power-off button doesn't, so I can't change accounts.

The weird thing is that, every time I press the reboot button at this point, Ubuntu does load in the normal way..

Still, I think it takes too long to start my pc..

Does anyone know a solution?

Many thanks (and a merry christmas)


Edit: btw, it's Gutsy 64-bit

---

### Post by kdarkentity on 2007-12-25
well i don't have any experience with 64 bit , but i have had troubles like this in the past where the usplash screen appears, starts loading and then my screen goes blank. But then usually if i booted into recovery mode it would automaticly fix the error (s). Did you install any new programs or packages recently?

---

### Post by |Porsche on 2007-12-25
Have you tried to boot with nosplash to see if where exactly it gets hung up?

---

### Post by oscarsfriend on 2007-12-25
I think there was a kernel security update recently for Gutsy.  Chances are it overwrote your /boot/grub/menu.lst with one that is b0rken.  Take a look at the backup (menu.lst~) and look for any differences and modify the menu.lst (make a second backup first), or restore the backup (that will use the previous kernel, though).

---

