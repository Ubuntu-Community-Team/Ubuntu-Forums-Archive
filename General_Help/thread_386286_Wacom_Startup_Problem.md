---
title: "Wacom Startup Problem"
date: 2007-03-16
forum: General Help
---

### Post by osarusan on 2007-03-16
Hi,

I'm having a weird problem with my Wacom Cintiq Tablet. I've got it working correctly in Edgy, but for some reason, it doesn't always load correctly on startup. That is, when Ubuntu loads, the pen behaves erratically, and doesn't cover the whole screen as it should. However, if I log out and then log back in, everything works just fine.

How come it doesn't load properly when I first start x? And is there a way I can fix this? It's a pain to have to log in and log out then log in again...

Thanks.

---

### Post by fragos on 2007-03-17
There's a configuration parameter for whole screen vs a portion separately for cursor, stylus, eraser and pad.  These can be set in Gimp and Inkscape differently.  I believe they can also be set in xorg.conf perhaps again differently.  I would wonder if this has something to do with your problem.  I haven't seen what you describe.  Also by default Device pad isn't included in xorg.conf and that impacted the functioning of buttons on the pad itself.

---

