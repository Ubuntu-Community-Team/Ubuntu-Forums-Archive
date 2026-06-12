---
title: "pipes and dialog boxes/crosshair window choice"
date: 2007-08-09
forum: General Help
---

### Post by element42 on 2007-08-09
Hi,
I'm using fluxbox in a standard ubuntu feisty install. I want to get a 'force kill' in the menu, like in gnome. I can kill an application from the terminal using pkill. I also know *about* pipes | but I don't really know how to use them. Also I would need to know a window choosey function.
 I guess my command would be something like ```
*window choose* | pkill
```.
Can anyone help? thanks!

---

### Post by RedSquirrel on 2007-08-09
What about xkill?

```
[exec] (xkill) {xkill} <>
```

If you put that in your menu, it will change your mouse cursor into a skull & crossbones and you can just click on the window of the application you want to kill.

---

### Post by element42 on 2007-08-10
That's a much easier way of doing things, and it certainly works just like I wanted; thanks!

---

### Post by RedSquirrel on 2007-08-11
You are most welcome.

Just remember the warning from 'man xkill':

"Xkill  is a utility for forcing the X server to close connections to clients.  This program is very dangerous..." :evil: :grin:

---

