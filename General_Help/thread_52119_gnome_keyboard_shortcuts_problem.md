---
title: "gnome keyboard shortcuts problem"
date: 2005-07-26
forum: General Help
---

### Post by GaWin on 2005-07-26
Hello everybody,

I just installed Ubuntu on my laptop, and after setting some (not very clever) keyboard shortcuts in the gnome menu, such has "space" = play, I cannot disable them.

Actually, i disabled them in the gnome menu, and they are marked as disabled, but they are actually still enabled and it makes it impossible to use the keys normally...

Any idea?

---

### Post by frodon on 2005-07-26
Go to Application>System Tools and open Gconf editor (sorry for the name, i have a french version). In apps>metacity>global_keybindings you could find the shortcuts you want to disable.

---

### Post by GaWin on 2005-07-26
Ok thanks. I have french version too anyway ;)

I disabled (even though they were already empty) all the faulty keybindings in Metacity and in gnome-setting and rebooted and now it works fine :) But I am not sure what solved it cause i had already rebooted before...

Thanks anyway...

---

