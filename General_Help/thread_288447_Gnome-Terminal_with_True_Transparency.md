---
title: "Gnome-Terminal with True Transparency"
date: 2006-10-29
forum: General Help
---

### Post by volanin on 2006-10-29
I installed Edgy today from scratch.
I just set the gnome-terminal to have a transparent background,
but I only got pseudo-transparency, even now with gnome 2.16.

Is it possible to have true transparency?
(Without the jagged background redraw and being able to see other windows behind.)

I have an 915GM Intel Graphics and Composite is enabled in xorg.conf.
No compiz/beryl installed.

---

### Post by Dr. Nick on 2006-10-29
I get true transpareny only when using beryl, if using metacity its just psudeo, I dont know of a way to get true transparency with metacity

---

### Post by TheMono on 2006-10-29
It is impossible (to the best of my knowledge) to get true transperancy with metacity. Compiz / Beryl will though.

---

### Post by Dr. Nick on 2006-10-29
True transparency terminal worked by just installing beryl, I guess it "intercepts" fake transparency and makes it real, If i disable beryl it goes back to psuedo.

---

### Post by volanin on 2006-10-30
Thank you for the answers!
I just found the explanation in another forum thread (whose link I have no longer...)

It seems Metacity already has support for true transparency and another few
neat effects, but they are quite experimental and somewhat broken yet, so
they were not compiled in for Edgy. Maybe in Feisty then!

Ok ok... where are those Beryl how-tos now?
:D

---

### Post by Bill Cosby on 2007-06-13
Well, I use **xcompmgr** and **Openbox 3.4.1**, they support all the fancy stuff, but how do I actually enable transparency for gnome-terminal? Or do I have to use a program like transset? The transparent effect is away when I close the window, can I make it start transparent?

---

