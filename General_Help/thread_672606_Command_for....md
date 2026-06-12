---
title: "Command for..."
date: 2008-01-19
forum: General Help
---

### Post by yxrkt on 2008-01-19
...for sending a WM_CHAR message (or whatever it's called in linux)

---

### Post by yxrkt on 2008-01-19
or is it possible to map one key to another? when i press "super + q", i want the comp to think i pressed "numpad 7"

---

### Post by yxrkt on 2008-01-19
no ideas? :confused:

---

### Post by artships on 2008-01-20
I think you're talking about xmodmap.  I havea a Sun keyboard with 12 function keys to the left of the regular one.  In a startup script I have:

xmodmap .sun_keys

The file contains:

keycode 232 = F11
keycode 133 = F12
keycode 134 = F13
keycode 135 = F14
keycode 140 = F15
keycode 248 = F16
keycode 191 = F17
keycode 192 = F18
keycode 122 = F19
keycode 188 = F20
keycode 160 = m

Use "xev" in an xtern to see what keycode is generated when a key is pressed (and released).

---

### Post by yxrkt on 2008-01-20
at last a response! thank you very much!

so if i want to map "super + q" to numpad 7 i can add 

```
keycode 115 = 79
```

to my startup xmodmap file?

---

### Post by yxrkt on 2008-01-20
so i read the whole xmodmap manual. it would seem we can only map a single key to another one.

---

