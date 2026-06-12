---
title: "keyboard problems eupean"
date: 2008-04-18
forum: General Help
---

### Post by jespor on 2008-04-18
hej

some weeks ago i accidental changed my resolution for my screen.
for a couple of hours ago i manege to fix it.
i used > sudo dpkg-reconfigure xserver-xorg
now some of the keys on my keyboard doesn't work like "menu", "Æ", "Ø" and "Å"
this is very anoying when writing danish
i get this error report

> error when activating  XKB-configuration.
this can have multiple reasons:
- an error in libxklavier
- an error in X-serveren (xkbcomp, xmodmap programmerne)
- a X-server with incompatible libxkbfile-implementation

X-server-versionsdata:
The X.Org Foundation
10300000
if you choose to report the error, please include:
- result of xprop -root | grep XKB
- result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd



sory for the bad spelling... i'm danish

---

