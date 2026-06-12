---
title: "Desktop Effects with Xinerama?"
date: 2008-05-11
forum: General Help
---

### Post by tsunamikitsune on 2008-05-11
My current setup consists of two LCD monitors (one connected through DVI, the other through VGA) on an Nvidia GeForce 7300 GT graphics card. I have them both enabled with Xinerama on Ubuntu 7.10.

Now, I've read in a few places that Desktop Effects don't work with Xinerama enabled. I've tried Twinview instead, but my monitors are two different sizes, so there's dead space when using Twinview. I'd like to stick with Xinerama, but I would also like to use Compiz.

Is there anyway to do this? If not, is there an alternative to Compiz?

---

### Post by crdlb on 2008-05-12
The nvidia driver does not support the Composite extension when Xinerama is enabled; this is unlikely to change. Xinerama is pretty much a hack; many (all ?) drivers have problems with it in some way. In previous versions of X, compiz would just segfault in an early opengl call, but now composite is correctly disabled. No composite manager will work, not even metacity's composite manager.

It is worth noting that you can use distinct X screens if you so desire (exactly the same setup as Xinerama, just with Xinerama disabled), but you will not be able to move windows between screens. That works pretty well, although there may be some issues with things taking longer on the second screen (an nvidia bug unless I'm mistaken).

---

