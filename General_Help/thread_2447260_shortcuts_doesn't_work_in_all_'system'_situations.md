---
title: "shortcuts doesn't work in all 'system' situations"
date: 2020-07-15
forum: General Help
---

### Post by simba4 on 2020-07-15
Hi all,

I would like to consult with you about a situation regarding simulating mouse buttons through system shortcuts.

F5 = xdotool click 1 (or xte mouseclick 1)
F6 = xdotool click 2 (or xte mouseclick 2)
F7 = xdotool click 3 (or xte mouseclick 3)



It works, but not in 'all situations'
For instance, in firefox upper bar, F7 won't work (as right click)
also, even when the sub_menu is open -  F5 (as left click) does not work.


There is an extension to this, but let's get some answers first.



[ATTACH=CONFIG]286473[/ATTACH]

Thank you,

James

---

### Post by Holger_Gehrke on 2020-07-16
If this is about using the keyboard instead of the mouse, you might want to take a look at [this]("https://linuxreviews.org/HOWTO_use_the_numeric_keyboard_keys_as_mouse_in_XOrg"). Since it's part of the very lowest level of the input system, it always works.

If this is about automation, the menu shown in your picture is part of the window manager, not the application. xdotool has specific functions to do the things this menu offers. See the man page of xdotool for details.

Holger

---

