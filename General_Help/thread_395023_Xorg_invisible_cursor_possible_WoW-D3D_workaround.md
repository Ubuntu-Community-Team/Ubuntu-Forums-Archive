---
title: "Xorg invisible cursor: possible WoW-D3D workaround?"
date: 2007-03-27
forum: General Help
---

### Post by zaubara on 2007-03-27
Hey!

I am looking for a working method to hide my cursor, making it invisible or apply a blank theme - I tried various things now, but not a single one worked for me.

I'd like to play World of Warcraft with wine in D3D (for better performance) on ubuntu, but there's that second (system-) pointer that makes it unplayable.

*) Transparent cursor theme:
[http://projects.o-hand.com/matchbox/sources/utils/xcursor-transparent-theme-0.1.1.tar.gz](http://projects.o-hand.com/matchbox/sources/utils/xcursor-transparent-theme-0.1.1.tar.gz)
Problem: Shows up correctly in gcursor, but applying the theme makes absolutely no difference. I still get the "Human" cursor theme.
*) Create a blank Cursor ([http://wiki.x.org/wiki/AdvancedTopicsFAQ](http://wiki.x.org/wiki/AdvancedTopicsFAQ)) and apply it to X with: xsetroot -cursor emptyCursor.xpm emptyCursor.xpm
Problem: Does work fine on _some_ parts of gnome only, ie. my cursor gets invisible when hovering over taskbars, the gnome application bar, ... but not inside any window (including WoW).
I even tried to create a new X instance on another display, so I had only that X-cursor to hide... no go.
*) Starting up X with no cursor theme
Problem: I was browsing the manpages for some super-special command to boot up X with no shown cursor (my launch-wow.sh includes that for improved performance what-so-ever), but I didn't find anything yet.

Any ideas? :(
Huge thanks in advance!

---

### Post by zaubara on 2007-03-29
Noone? :(

Buying cedega should probably not be the only alternative...

---

