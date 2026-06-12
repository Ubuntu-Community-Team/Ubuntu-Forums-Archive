---
title: "Getting scrollbar arrows in XFCE4 Terminal"
date: 2013-05-18
forum: General Help
---

### Post by chellrose on 2013-05-18
I recently installed Xubuntu 12.04.  (It's my first time with XFCE; I'm a longtime KDE3/Trinity user :-).)  The default terminal, XFCE4, is pretty nice and does everything I'd like it to do, except that the scrollbar is missing its up/down arrows.  You know, the arrow you can click on to scroll up/down by one line, or press and hold to scroll further.

There is a scroll _bar_ which I can click and drag to scroll up or down, but that's a pain with the touchpad.  Or I can click above/below the bar to jump up or down by several lines.  That usually jumps it too far, though.

Does anyone know if there's a way to get the arrows on the scrollbar (aside from using a different terminal program)?

---

### Post by dentaku65 on 2013-05-18
Try to disable overlay scrollbar, if I recall well in 12.04:
```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```

---

### Post by Dennis N on 2013-05-18
> **Sissy13 said:**
> I recently installed Xubuntu 12.04.  (It's my first time with XFCE; I'm a longtime KDE3/Trinity user :-).)  The default terminal, XFCE4, is pretty nice and does everything I'd like it to do, except that the scrollbar is missing its up/down arrows.  You know, the arrow you can click on to scroll up/down by one line, or press and hold to scroll further.

Does anyone know if there's a way to get the arrows on the scrollbar (aside from using a different terminal program)?

The lack of arrows comes with the theme in use. Choose another theme if you must have arrows. Clearlooks is a one theme which will give you arrows on the scrollbar of the terminal and file manager.

Settings Manager > Appearance > Style > Clearlooks

Clearlooks is not necessarily the only choice you have - Bluebird is another. Try some others.

---

### Post by chellrose on 2013-05-22
Thanks! :)

---

