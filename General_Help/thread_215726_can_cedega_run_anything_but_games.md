---
title: "can cedega run anything but games?"
date: 2006-07-14
forum: General Help
---

### Post by slimdog360 on 2006-07-14
I was just wondering if anyone knows if cedega can emulate anything other than just games. I have a circuit simulator, electronics workbench, thats a windows only program and doesnt run properly under either wine or crossover office.

---

### Post by aysiu on 2006-07-14
As far as I know, Cedega is just a games-oriented and tweaked version of Wine.

Wine is the general program that helps you run Windows programs.

Crossover Office can usually run programs that Wine cannot.

---

### Post by YokoZar on 2006-07-15
> **aysiu said:**
> As far as I know, Cedega is just a games-oriented and tweaked version of Wine.This isn't quite accurate.  Cedega is a completely different program that is based off a very old version of Wine from before Wine adopted the LGPL license.  Every update to Wine since then has *not* gone into Cedega.

Cedega and Wine are now developed seperately, and code is not shared between them - Cedega using a proprietary approach, and Wine an open source one.

> Wine is the general program that helps you run Windows programs.

Crossover Office can usually run programs that Wine cannot.
Crossover Office, on the other hand, is based on the open source version of Wine.  Crossover Office is, essentially, a tested and supported version of Wine, much like Ubuntu is a tested and supported version of the Linux kernel, Gnome, and a bunch of other apps.

Codeweavers, the company that markets Crossover Office, actually pays for the majority of Wine development, hiring developers to work full time on the free version of Wine (as well as a few to make sure that their supported version works with their supported apps).  This is not too dissimilar from the way that Linux distribution vendors (eg Red Hat) pay people to improve the Linux kernel itself, which helps improve *all* distributions.

---

