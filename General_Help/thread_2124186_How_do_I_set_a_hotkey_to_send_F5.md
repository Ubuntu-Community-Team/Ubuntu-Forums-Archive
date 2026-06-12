---
title: "How do I set a hotkey to send F5?"
date: 2013-03-10
forum: General Help
---

### Post by weehooherod on 2013-03-10
I need to set a hotkey so that when I press Ctrl+F5 then F5 is registered. I will be doing this for all 12 function keys (Ctrl+1 for F1, Ctrl+2 for F2, and so on). Does anybody know how to do this with xev, an .sh file, the built in shortcut settings, anything? Thank you for the help!

Ubuntu 12.10
ASUS UX31e Zenbook with BIOS 214

---

### Post by LewisTM on 2013-03-10
Install package **xdotool**.
Next associate your shortcuts with xdotool commands.
For instance, Ctrl-1 can be bound to command
```
xdotool key F1
```
Cheers!

---

### Post by weehooherod on 2013-03-10
Perfect! Thank you so much.

---

### Post by weehooherod on 2013-03-10
Actually that didn't quite do it for me. I have F5 remapped to lower the brightness of my screen. When I set CTRL+F5 to send F5 it too lowers my screen brightness. My final goal is to have CTRL+F5 just send F5 so I can refresh pages and such.

---

### Post by LewisTM on 2013-03-10
Is it Ctrl-F5 or Ctrl-5?
Pressing F5, either through xdotool or physically, will send the F5 keystroke and trigger any associated event. There is no way around that. Just unset the brightness binding if you want to keep only one action. Maybe set it to Super+F5 or something.

---

