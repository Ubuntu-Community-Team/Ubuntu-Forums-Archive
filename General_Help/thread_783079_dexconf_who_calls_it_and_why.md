---
title: "dexconf: who calls it and why?"
date: 2008-05-05
forum: General Help
---

### Post by radu.c on 2008-05-05
Hi,

Does anyone know who calls dexconf and why when I already have a working Xorg.conf?

I have a custom setup where I use xinit directly and, in this case, kdm is disabled, but from time to time X decides to not start (it starts on a second attempt). Some times, this triggers a call to dexconf and overwrites my xorg.conf, but I can't for the life of me figure out who calls it so I can disable this behavior (I used grep on the whole filesystem, and still nothing relevant).

Any ideas?

---

