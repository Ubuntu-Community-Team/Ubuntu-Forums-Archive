---
title: "Hibernation/Suspend news"
date: 2007-07-02
forum: General Help
---

### Post by ago on 2007-07-02
I had a reply from mjg59 (ubuntu kernel dev). Bad news indeed:

* Hibernation is a no go for us (swap on a loopmounted file cannot be supported). So we will disable it.
* Suspend will not work with a userspace filesystem (since other processes might want to access the drive after fuse is frozen, and the order is not easy to change), which means that you cannot have suspend when the virtual files are on ntfs (it should work already on fat32, please try it out, you need a large enough swap > memory), so we will disable it conditionally.

---

### Post by Gan on 2007-07-03
This is indeed a sad news. But anyway thanks for the work!

---

