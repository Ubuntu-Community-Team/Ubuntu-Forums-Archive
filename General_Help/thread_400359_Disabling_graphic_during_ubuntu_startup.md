---
title: "Disabling graphic during ubuntu startup?"
date: 2007-04-03
forum: General Help
---

### Post by khughitt on 2007-04-03
Hi,

Does anyone know if there is a way to temporarily (or permanently) disable the Ubuntu graphic during boot-up? I'm trying to see what is slowing down the boot process, but i haven't been able to figure out how to hide the graphic, and list the services, etc as they are loading. 

Is there any keyboard command or configuration setting to to show services loading?

Thanks!

---

### Post by hardyn on 2007-04-03
remove 'splash' from boot string in /boot/grub/menu.lst and add 'verbose'

---

### Post by kevpatts on 2007-04-03
or if you want to do it as a once off, when the grub screen appears, press 'e' when the default linux config is highlighted, then scroll to the second line and press 'e' again. Remove the words 'quiet' and 'splash' and add 'verbose' as hardyn said. Then press 'b' to boot once it's edited.

This will then continue to boot normally next time, you won't have to change anything back.

---

### Post by khughitt on 2007-04-03
cool. thanks- now i know why init is taking so long.. just gotta figure out how to fix that :)

---

### Post by cisforcojo on 2007-04-04
You can also use 'dmesg'.

Type that in a terminal and that's MUCH better for seeing what happened. You don't have to quickly catch things as they scroll by.

---

### Post by shotgunefx on 2007-04-04
Install bootchart if you want to know what's taking so long ;)

---

