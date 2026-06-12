---
title: "How to make filesystem writable from recovery root terminal."
date: 2013-04-18
forum: General Help
---

### Post by captainwithershins on 2013-04-18
Ubuntu update broke my video again(stop installing other drivers over my ATI ones). I want to reinstall mine but ths root console from recovery says ths file system is read-only. Ubuntu boots normally in a black or the loading screen.

---

### Post by captainwithershins on 2013-04-18
mount -o remount,rw / worked.

---

