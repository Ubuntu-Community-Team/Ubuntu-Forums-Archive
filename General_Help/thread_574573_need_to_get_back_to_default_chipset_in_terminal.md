---
title: "need to get back to default chipset in terminal"
date: 2007-10-13
forum: General Help
---

### Post by perfect_circle on 2007-10-13
i edited the chipset to try and fix my resolution, and appearently i chose the wrong one...my bad.  i was certain i had the i810 chipset. but i need to know how to set it back to default. so how do i get to it to edit it. and how do i correctly identify the correct chipset? thanks.

---

### Post by bodhi.zazen on 2007-10-13
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Will select defaults for everything but resolution.

---

