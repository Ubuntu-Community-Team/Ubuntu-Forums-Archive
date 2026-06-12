---
title: "glabels 3.0.0 font selection horribly slow"
date: 2012-10-26
forum: General Help
---

### Post by jejones3141 on 2012-10-26
glabels is a very useful program... but it seems that now that I've moved to 12.10, font selection in glabels is as slow as molasses.

glabels 3.0.0, which 12.10 comes with, has a new font selection widget, and I suspect that this is the source of the slowdown.

Has anyone found a way to speed up font selection for glabels 3.0.0?

---

### Post by dino99 on 2012-10-26
thats the latest changes made on Sept 12:

  * debian/patches/0008-build-with-new-eds.patch:
    - build with latest e-d-s/ebook API

maybe you need to report that issue. Do you have evolution installed too ?

---

### Post by jejones3141 on 2012-10-26
Thanks. I don't have evolution installed, but I do have evolution-data-server and evolution-data-server-common installed. Just submitted the bug on launchpad.

([https://bugs.launchpad.net/ubuntu/+source/glabels/+bug/1071808](https://bugs.launchpad.net/ubuntu/+source/glabels/+bug/1071808) for those interested.)

---

