---
title: "ld cannot find -lGL 18.10"
date: 2018-12-04
forum: General Help
---

### Post by cjdg on 2018-12-04
Hi i want to compile some programs but ld cant find -lGL

---

### Post by spjackson on 2018-12-04
Do you have /usr/lib/x86_64-linux-gnu/libGL.so ? This should be provided by the package libgl1, so if you don't have it, you could try installing that. However, I would normally expect this to be installed by a typical desktop install. If you do have the library and your compilation isn't finding it, perhaps it is affected by some the link flags you are using.

---

