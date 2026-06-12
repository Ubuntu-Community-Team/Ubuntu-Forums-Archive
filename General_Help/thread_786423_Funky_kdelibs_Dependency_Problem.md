---
title: "Funky kdelibs Dependency Problem"
date: 2008-05-08
forum: General Help
---

### Post by treehouse on 2008-05-08
I have a kmuddy deb file that I wish to install. Here's what I get when I try to install it:

```

Unpacking kmuddy (from .../nicholas/Desktop/kmuddy.deb) ...
dpkg: dependency problems prevent configuration of kmuddy:
 kmuddy depends on kdelibs4c2a (>= 4:3.5.8-1); however:
  Version of kdelibs4c2a on system is 4:3.5.8-0ubuntu3.4.
dpkg: error processing kmuddy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kmuddy

```

and gdebi gives me a "dependency not satisfiable" for it too.

I've checked for upgrades and this appears to be the highest Synaptic will give me...

---

### Post by treehouse on 2008-05-09
Solved it myself by including Hardy repositories and then upgrading.

---

