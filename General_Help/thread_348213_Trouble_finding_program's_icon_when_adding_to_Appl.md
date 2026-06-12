---
title: "Trouble finding program's icon when adding to Applications menu [Resolved]"
date: 2007-01-28
forum: General Help
---

### Post by indigoshift on 2007-01-28
Okay, here's the deal:

1:  I installed FontForge via Synaptic, which installed just fine.

2:  I decided to add FontForge to my Applications menu, so I wouldn't forget that I installed it. ;)

3:  Had no problem using Alacarte to do this, except for one thing:  I can't find the FontForge icon on my system.

When I Alt+F2 for FontForge, I can see the icon, but can't find that icon to tell Alacarte to use it when I add FontForge to my Applications menu.

Is there a default place where these are stored?  If not, where should I look?

EDIT:  Looks like there's really no need, as FontForge already shows up under "Programming" under the Applications menu, but I'd still like to know how to search for icons, in case I run into this in the future.  ;)

EDIT 2 (ELECTRIC BOOGALOO):  Could it be "/usr/share/icons", perhaps?

Sorry for mucking up the forums.  :)

---

### Post by aysiu on 2007-01-28
I think you're on the right track. /usr/share/icons is one place to look. I think they can also be in /usr/share/pixmaps. One thing you can try is ```
sudo updatedb
locate fontforge
``` to see where the icons might live.

Of course, you could always just put a FontForge icon somewhere and use that.

---

### Post by indigoshift on 2007-01-29
Yeah, I found it (see Edit 2 above).

I love this OS for that:  it thinks like I do.  I'd explain, but I don't know if I can, really. ;)

---

