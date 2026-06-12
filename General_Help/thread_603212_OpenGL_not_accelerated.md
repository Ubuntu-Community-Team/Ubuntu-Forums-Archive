---
title: "OpenGL not accelerated?"
date: 2007-11-04
forum: General Help
---

### Post by Angelbeast on 2007-11-04
I am running OpenGL and have 3D acceleration enabled. However when i run VariCad i get a window when it starts saying that OpenGL is NOT accelerated. Do i need to do something to a config file somewhere?

---

### Post by troyer81 on 2007-11-09
It looks like your laptop (based on your signature) has an ATI graphics card.  Last time I checked, the default ATI drivers (i.e. opensource) did not support 3D acceleration, even if you "enable" it in the options.  The alternative is to use the drivers provided by ATI.  Rather than step you through that process, do a search on the forums for installing the fglrx drivers for ATI video cards.  The downside is that the proprietary drivers are a little less stable, but they do allow the 3D acceleration.  If you can't find anything, let me know and I'll do a little more research to point you in the right direction.

---

### Post by Angelbeast on 2007-11-10
> **troyer81 said:**
> It looks like your laptop (based on your signature) has an ATI graphics card.  Last time I checked, the default ATI drivers (i.e. opensource) did not support 3D acceleration, even if you "enable" it in the options.  The alternative is to use the drivers provided by ATI.  Rather than step you through that process, do a search on the forums for installing the fglrx drivers for ATI video cards.  The downside is that the proprietary drivers are a little less stable, but they do allow the 3D acceleration.  If you can't find anything, let me know and I'll do a little more research to point you in the right direction.

Well i actually do have the fglrx drivers installed, which is what's puzzling me.It seems to be accelerated for everything else such as the desktop effects and games but not for that one app...

---

