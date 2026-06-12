---
title: "complete theme saving"
date: 2008-05-05
forum: General Help
---

### Post by fredknex on 2008-05-05
Hi, I've been experimenting with custom themes lately and am wondering if it is possible to 100% save a custom desktop theme in gnome, including panels and their sizes/positions, animation settings,  etc.  For example if I wanted emulate the look of windows or osx just for kicks, it would be nice to have an easy way to switch back to my normal gnome desktop instead of manually changing panel heights and the like. I don't know if this is at all possible, but appreciate your any help you can give.

(this might be better posted on a gnome-specific site but uhh...yeah)

---

### Post by macaholic on 2008-05-05
I'm not sure how to do this, but I would love to know, since when I change or test distros it would be great to take my theme along with me in case I choose to keep using it.

---

### Post by NilsE on 2008-05-05
Themes and Icons are stored in folders by the same name as you select or create them within the following folders.

/usr/share/themes   and /usr/share/icons

or

in .themes and .icons folders in your home directory depending on how they were installed.

Therefore, you can archive at the folder level. When restoring just make sure the use folders option is on and just extract them to the theme or icon folders. The appearance preferences will find them automatically.

If your theme controls panels they will be part of the theme folders.

---

### Post by Genius314 on 2008-05-05
I was thinking the same thing. There should be some program that could change all the settings at once (including Metacity, GTK+, Emerald, Panel placement, Compiz settings, AWN settings, etc...).
I'd love to see something like that... of course, I'm not a programmer (yet).

---

