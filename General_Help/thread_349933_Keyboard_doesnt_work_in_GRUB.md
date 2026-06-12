---
title: "Keyboard doesnt work in GRUB"
date: 2007-01-30
forum: General Help
---

### Post by w0lf19 on 2007-01-30
I installed Ubuntu as a dual-boot with windows XP, and when the PC boots, I cannot select an OS in GRUB (theyre all listed there, but I cannot select between them with my USB keyboard). What can I do to fix this? I really need to get into my XP partition tonight to finish some work.

thanks

-w0lf

---

### Post by po0f on 2007-01-30
w0lf19,

Look in the BIOS settings for "Legacy USB support" or something like that and enable it.

---

### Post by vigleik on 2007-01-30
As an emergency fix if you don't have time to poke around in your bios right now, edit /boot/grub/menu.lst, put the windows partition first. That should boot you into windows next time you reboot.

On the other hand, maybe that's a bad idea. Because then you're stuck with windows until you figure out how to use your keyboard in grub. (Or you'd have to, say, boot from the live CD again to fix it.)

---

