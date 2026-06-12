---
title: "Firefox overlay-like scrollbars in Ubuntu 12.04"
date: 2013-06-01
forum: General Help
---

### Post by Isamu715 on 2013-06-01
I'm trying to install overlay-like scrollbars in Firefox from [here]("http://gnome-look.org/content/show.php/?content=146463"). On one of my previous installs I somehow managed to get them working but I don't remember how. Now I'm stuck again. I've tried following both the original instructions and the ones posted in a comment on gnome-look. Both result in the scrollbar just getting resized. I've tried to move the scrollbars folder and it's content around but to no avail. It seems that it can't load/find the scrollbar image files. What am I doing wrong?

---

### Post by tc424 on 2013-06-23
> **Isamu715 said:**
> I'm trying to install overlay-like scrollbars in Firefox from [here]("http://gnome-look.org/content/show.php/?content=146463"). On one of my previous installs I somehow managed to get them working but I don't remember how. Now I'm stuck again. I've tried following both the original instructions and the ones posted in a comment on gnome-look. Both result in the scrollbar just getting resized. I've tried to move the scrollbars folder and it's content around but to no avail. It seems that it can't load/find the scrollbar image files. What am I doing wrong?

I've just got it working, needed to install [gtk2-engines-pixbuf]("apt:gtk2-engines-pixbuf"), which at least on 12.04 doesn't seem to be installed by default.

S.

---

### Post by Isamu715 on 2013-06-23
Thanks, that did it, works great now :D

---

