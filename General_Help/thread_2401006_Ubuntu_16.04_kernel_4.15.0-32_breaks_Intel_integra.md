---
title: "Ubuntu 16.04 kernel 4.15.0-32 breaks Intel integrated graphics"
date: 2018-09-12
forum: General Help
---

### Post by godatum2 on 2018-09-12
The kernel 4.15.0-32-generic is missing the 4.15.0-32 image extra. Also, the Intel integrated graphics driver is broken.

Running lshw -c video brings back *-display UNCLAIMED

There is no video driver.

When rolling back to 4.15.0-15 the Intel graphics works and there is the correct video driver.

I am running 50 laptops all HP 840 G3. This happens on all 50 laptops. They have the Intel HD Graphics 520.

---

### Post by godatum2 on 2018-09-13
Anyone able to offer advice or help? This is quite a serious issue.

---

