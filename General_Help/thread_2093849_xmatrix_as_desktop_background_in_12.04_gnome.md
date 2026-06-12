---
title: "xmatrix as desktop background in 12.04 gnome"
date: 2012-12-12
forum: General Help
---

### Post by ntzrmtthihu777 on 2012-12-12
[FONT=Courier New]Hello,

Attempting to set xmatrix as desktop background in Ubuntu 12.04.
I have removed unity completely and am using GNOME Classic.
I have googled and searched the forums extensively on this subject to no avail.
I have had success with using glmatrix as a desktop background with this code:
[/FONT]```
[FONT=Courier New]xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -window-id WID[/FONT]
```[FONT=Courier New]but this produces a 3-D effect; where xmatrix creates the 2-D effect I desire. Any help and/or feedback you could provide would be greatly appreciated.

[EDIT] Using GNOME Classic with no effects allows for it, you can run
[/FONT]```
[FONT=Courier New]/usr/lib/xscreensaver/xmatrix -root[/FONT]
```
[FONT=Courier New]Allows it to work.[/FONT]

---

### Post by ntzrmtthihu777 on 2013-01-04
Apparently doing this disagrees with compiz on some level, so running with no effects prevents this disagreement

---

