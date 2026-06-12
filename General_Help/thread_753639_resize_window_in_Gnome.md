---
title: "resize window in Gnome"
date: 2008-04-12
forum: General Help
---

### Post by mordi05 on 2008-04-12
I wonder, in GNOME is there a way to enlarge the field in the corner/sides of a window in which you can click+drag to resize it? 

The bottom-left corner is generally ok, but the top/side fields are slim. It is like I have to hit one pixel on the side with the pointer to be able to resize it. With my touchpad I frequently have to try multiple times. Probably not a problem with a regular mouse.

Would it help to increase borders?

---

### Post by Tyke91 on 2008-04-12
don't know how to increase that size, but i know that alt+middle click or alt+left+right click on a laptop will instantly go to resize...

---

### Post by mordi05 on 2008-04-12
Ok, thank you, but that doesn't seem to work here. I can alt+right click and then choose resize from the dropdown but that is kind of tedious. Also, it seems like I have to confirm the resize with enter.

---

### Post by chewearn on 2008-04-12
The width of the window borders depend on the gnome theme you are using.  Choose one that gives you wider width.

---

### Post by mordi05 on 2008-04-12
Ok, thanks.
But I love my current theme. Any way to easily edit such parameters in a theme, or is it a whole ordeal?

I think I've seen borrderless themes around. Are there no "resize fields" for windows when using those then?

---

### Post by chewearn on 2008-04-13
I found a "solution": I haven't personally done this, because I'm using compiz-emerald instead of metacity.

If you look under /usr/shared/themes/ you will find the various themes installed in your system.  Under the theme subdirectory (e.g. Simple, Crux, Glossy...), you find metacity-1/metacity*.xml files.  I think the adjustments you are looking for are in there.  Not the easily point click method, but I believe Gnome is build this way on purpose.

On your second question, I think those borderless themes probably has 1px border.

Documentations, if you are interested:
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

---

### Post by mordi05 on 2008-04-13
Thank you. I'll play around with it.

---

