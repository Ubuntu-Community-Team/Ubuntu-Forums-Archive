---
title: "Monitor AOC i-menu for Linux"
date: 2013-08-25
forum: General Help
---

### Post by d2btoo on 2013-08-25
Hello,

My new monitor comes with this "i-menu" software for adjusting brightness, contrast etc. Trouble is this only works under Windows, so any idea how I can use this thing under Ubuntu! Thanks.

Monitor Model: AOC E1670SW
[Screen-shot of i-menu](http://i.imm.io/1g3qI.png)

---

### Post by d2btoo on 2013-08-26
*bump*

---

### Post by d2btoo on 2013-08-27
It seems under 12.04 I can use this:
```
xrandr --output VGA1 --brightness 0.50
```
--this is not optimal solution, but works for the moment.

Now, how can I achieve this under 10.04 (the [COLOR=darkred]--brightness[/COLOR] switch doesn't work under 10.04 right!)?

**EDIT:** Found [COLOR=darkred]gnome-color-manager[/COLOR] can at-least control brightness and contrast in 10.04. It's not perfect but it can dim the screen for now.

---

