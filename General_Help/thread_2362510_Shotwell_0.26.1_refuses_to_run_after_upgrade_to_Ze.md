---
title: "Shotwell 0.26.1 refuses to run after upgrade to Zesty"
date: 2017-05-29
forum: General Help
---

### Post by ka1ssr on 2017-05-29
I’ve been having trouble getting Shotwell to run since upgrading to Zesty. Running from a terminal, I get the following error message:

```
shotwell: error while loading shared libraries: libraw.so.15: cannot open shared object file: No such file or directory
```

Running locate for libraw.so finds libraw.so.16, so it would seem that Shotwell is looking for an earlier version of libraw.

Suggestions welcome. Many thanks.

---

### Post by mc4man on 2017-05-29
You may (likely) have shotwell from a ppa. So when you upgraded it stayed as current version in 17.04 is 0.22 
So remove current version or check if ppa used has a zesty package. If so add ppa & upgrade shotwell.
(- for instance this ppa does - [https://launchpad.net/~yg-jensge/+archive/ubuntu/shotwell/](https://launchpad.net/~yg-jensge/+archive/ubuntu/shotwell/)

---

