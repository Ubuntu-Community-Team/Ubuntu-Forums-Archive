---
title: "Broken Packages - Can not fix"
date: 2007-03-24
forum: General Help
---

### Post by sdgreen on 2007-03-24
Confused.

Upgraded from Dapper to Edgy - initially no problems. All of a sudden 2 broken packages appeared however can not fix either through synaptic or via apt. When I try to remove the offending packages or re-install, the system will report error and cannot proceed. What to do?

Error:
[COLOR="Red"]E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[/COLOR]
Packages:

[COLOR="Blue"]dc version 1.06-19ubuntu1 GNC dc arbitrary precision rpn calculator
debianutils 2.16.2 Misc utilities[/COLOR]

If I mark for reinstallation, Synaptic reports it wants to remove some 600 plus packages some of which are essential.

Help.:confused:

---

### Post by usien on 2007-03-24
i don't know if it goes without saying in your post but have you tried
edit -> fix broken packages 
from synaptic

---

### Post by sdgreen on 2007-03-24
Yes tried that with the error generated in my first post.

There must be some sort of console command that forces a fix, but no idea what it might be.

---

### Post by zvacet on 2007-03-25
Maybe this will help
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by sdgreen on 2007-03-25
zvacet:

Why you are a genius!  Your suggestion seemed to work.

thanks greatly.

---

