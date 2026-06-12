---
title: "Firefox is sluggish"
date: 2007-10-15
forum: General Help
---

### Post by irieken on 2007-10-15
It seems that Compiz doesn't like certain graphics cards, and that causes programs like Firefox to lag fairly dramatically when you try to scroll.

To check if this is the case, type "metacity --replace" in terminal to switch to Metacity window manager. If that doesn't fix things, type "compiz --replace" to switch back.

If Metacity seems a lot more responsive, and you feel that losing Compiz isn't too much of a sacrifice, you can make Metacity the default window manager. To do this, edit /usr/bin/gnome-wm as root, and set DEFWM to /usr/bin/metacity 

Took me a while to figure this out, so I hope that it saves someone else some time.

---

### Post by santiagoward2000 on 2007-10-15
Hey, great idea!
While we are at this, is there any lighter browser you would recommend? I tried Opera, it's not bad at all.

---

