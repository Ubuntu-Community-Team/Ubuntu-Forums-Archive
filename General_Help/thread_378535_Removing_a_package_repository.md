---
title: "Removing a package repository?"
date: 2007-03-07
forum: General Help
---

### Post by StereoHeathen on 2007-03-07
How do I do this, as I've accidentally added one twice?

---

### Post by taurus on 2007-03-07
Put a # in front of the line or remove it with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by StereoHeathen on 2007-03-07
Thanks, that's exactly what I wanted.

---

