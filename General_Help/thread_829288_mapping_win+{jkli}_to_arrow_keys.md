---
title: "mapping win+{j|k|l|i} to arrow keys"
date: 2008-06-14
forum: General Help
---

### Post by h2g2 on 2008-06-14
Hi everyone!

I want to map <win+j> to <left arrow>, <win+i> to <up arrow> and so on, so i don't have to reach for the arrow keys. similar to vim except that it should work on the whole desktop. i took a look into xmodmap, but couldn't figure how to do it. Can anyone help please?

Thank you,

---

### Post by h2g2 on 2008-06-15
anyone?!

---

### Post by bigpook on 2008-11-12
Man, I am trying to do the same thing. Google is not being helpful either.

---

### Post by bigpook on 2010-05-08
keycode 51 = BackSpace
keycode 22 = backslash bar
keycode 133  = Mode_switch
keycode 34 = bracketleft braceleft Up
keycode 45 = k K Home
keycode 46 = l L Prior
keycode 47 = semicolon colon Left
keycode 48 = apostrophe quotedbl Right
keycode 59 = comma less End
keycode 60 = period greater Next
keycode 61 = slash question Down
keycode 108 = Alt_R
keycode 49 = Escape
keycode 9 = grave asciitilde




Stick the above in a file and then run xmodmap on that file.
The above emulates a HHKB layout, but you can modify it as you need to.

---

