---
title: "Loop device by SNAP without SNAP installed"
date: 2017-11-05
forum: General Help
---

### Post by alain.roger on 2017-11-05
Hi,

i have several snap loop devices appearing while i do not have snap or snapd installed.
Previously i had snap install but i removed all loop devices and snap as snapd.
for almost 6 or 7 months i had no loop device appearing and suddenly since upgrade from kubuntu 17.04 to kubuntu 17.10 several snap loops appeared.
Some for core, some for libreoffice, while i do not have snpad or snap installed, and that i have ppa for libreoffice.

here it is:
[IMG]http://i67.tinypic.com/14ky5g5.jpg[/IMG]

How to get rid of those loops definitively. Moreover it's very confusing in disk utility as in Dolphin apps those useless loops.

thx.

---

### Post by mc4man on 2017-11-05
Those are old versions of  snaps. i'd probably start by searching snap from / and see what you find
(- assuming dolphin does recursive searches?
One place to look would be /var/lib/snapd/snaps (-if that exists..

---

