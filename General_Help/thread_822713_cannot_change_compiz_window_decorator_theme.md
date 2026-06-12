---
title: "cannot change compiz window decorator theme"
date: 2008-06-08
forum: General Help
---

### Post by key on 2008-06-08
Hi All,

I am having some problems with the compiz window decorator under XFCE. I can change the 'theme' no prob from XFCE, but the actual window decoration does not change. Sometimes the color of the window decoration changes, but I am not sure why. 

Things behave as expected in gnome, and they carry over to some extent into XFCE but not completely. Regardless, I don't want to switch into gnome to change my window decor.

Anyone else dealt with this? Is there a window decoration theme manager for compiz that will load GTK themes?

---

### Post by Forlong on 2008-06-08
GTK themes are only responsible for the window's content -- not for the window boarders.

On Xfce, it's best to use Emerald
```
sudo apt-get install emerald
```
Run it with this command
```
emerald --replace
```
via [Alt]+[F2]

---

### Post by key on 2008-06-28
Thanks for the reply Forlong, that appears to be the best course of action for flexibility in theming compiz w/XFCE. Works well, stable, lots of nice themes at [www.gnome-look.org](www.gnome-look.org). I'm happy. :)

---

