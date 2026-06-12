---
title: "checkinstall: create package but don't install it"
date: 2012-11-04
forum: General Help
---

### Post by flapane on 2012-11-04
Any way to let "checkinstall" create a .deb package without installing it after the creation?
Thanks in advance

---

### Post by sanderj on 2012-11-04
> **flapane said:**
> Any way to let "checkinstall" create a .deb package without installing it after the creation?
Thanks in advance

First hit on Google says

> use the command line switch sudo checkinstall --install=no

So ... does that work?

---

### Post by flapane on 2012-11-04
Great, thanks, I see it works.
However, believe me or not, I made the same question a couple of years ago and it turned out that it DIDN'T work (it just kept installing the package) and the only solution was creating a deb package the old debian-ish way.
Luckily, I guess they fixed it in the meantime.

---

