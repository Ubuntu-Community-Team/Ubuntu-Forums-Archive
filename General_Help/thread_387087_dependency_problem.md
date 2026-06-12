---
title: "dependency problem"
date: 2007-03-17
forum: General Help
---

### Post by strivehosting on 2007-03-17
Okay, I managed to get it onto my Ubuntu desktop and when I tried to install it, it says "Error: Dependency is not satisfiable: sl-modem-modules-new|sl-modem-source|kernel-image-2.6"

What does that mean exactly? Please help me out, dialup is my only way to get online and I really want to switch over completely to Ubuntu.

---

### Post by mojoman on 2007-03-20
I'm not sure I quite got what you're trying to install but if something won't install or run due to a dependency problem (i.e. another package lower down in the hierarchy is missing) you can solve this with the following command:

```
sudo apt-get install --fix-broken
```

This, of course, assumes that you have an Internet connection or otherwise access to an installation media (e.g. CDs). 

best regards
/mojoman

---

