---
title: "Help Please... metacity gconf issue"
date: 2007-08-29
forum: General Help
---

### Post by Blue_T0oth on 2007-08-29
after punching this in terminal:           metacity --replace

Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is not a reasonable cursor_size; must be in the range 1--128
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


not sure how to fix this or even why i'm having this problem this is just after a fresh install with basic updates, i've reinstalled 7.04 and still have the same problem, i've removed and reinstalled metacity, reset the gconf auto with term command sudo dpkg-reconfigure -phigh xserver-xorg... i'm stuck here :((

---

### Post by bashologist on 2007-08-29
Those are just warnings and shouldn't effect much if anything negatively. My gconf-editor keys are the same except my cursor_size is 24.

---

### Post by Wolki on 2007-08-29
> **Blue_T0oth said:**
> Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is not a reasonable cursor_size; must be in the range 1--128
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Do the following alt-F2, "gconf-editor", return.

In the treeview on the left, go to /apps/metacity/window_keybindings/ and select toggle_shaded on the right. Right-click and choose "revert" (or simliar, not running the engllish version right now... should be the third entry)

then do the same for /desktop/gnome/peripherals/mouse on the left and cursor_size on the right.

I wonder why this happened though. Do you use desktop effects or something similar?

---

