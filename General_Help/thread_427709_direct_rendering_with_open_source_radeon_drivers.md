---
title: "direct rendering with open source radeon drivers"
date: 2007-04-29
forum: General Help
---

### Post by evilgold on 2007-04-29
Is it possible to get direct rendering working with the open source radeon (or ati) driver. I have an  integrated ATI Xpress 200m.

---

### Post by hermesrules on 2007-04-30
Hi,

Yes, it is possible, however I am not sure if you need to do something special. I don't remember having to do anything, it just worked, and I have a rather old ATI Mobility U1.

To check out whether you have direct rendering enabled, type in a terminal:

```
glxinfo | grep direct
```

The output of that should be something like:
```
direct rendering: Yes
```

Hope this helps.

---

### Post by trotur on 2007-04-30
> **evilgold said:**
> Is it possible to get direct rendering working with the open source radeon (or ati) driver. I have an  integrated ATI Xpress 200m.

If site [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) is up to date, it isn't possible to get 3D support for your card:
> **2D acceleration only**
Xpress 200M Northbridge integrated GPUs

---

