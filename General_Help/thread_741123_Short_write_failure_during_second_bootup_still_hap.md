---
title: "Short write failure during second bootup still happens with newest Wubi on fat32"
date: 2008-03-31
forum: General Help
---

### Post by steve196 on 2008-03-31
I still had to hand edit menu.lst, in order to change all instances of `rw` to `ro`.
The cd image i used is from the first beta release. I do not know, if another was released meanwhile. Wubi is from the Wubi website.

---

### Post by ago on 2008-03-31
hmmm very strange

can you please post /usr/share/initramfs-tools/scripts/local

---

### Post by ago on 2008-03-31
Ubuntu package is fine and includes the patch... Having ro or rw in menu.lst should not make any difference.

---

### Post by steve196 on 2008-04-01
Unfortunately, i have done an update (oddly enough, without a new kernel) and now i get "no such device" when it tries to mount the root filesystem. So i cannot access /usr at the moment.

---

