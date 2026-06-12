---
title: "Does anybody know how install mac apps on ubuntu???"
date: 2007-03-04
forum: General Help
---

### Post by aquinterop on 2007-03-04
Hi, i want to know how can i install mac apps on linux, because i have a hp scanjet scanner 4070, wich only have drivers for windows and mac, and wine doesnt work fine for de win driver. Thank you

---

### Post by jocko on 2007-03-04
I'm not sure it's possible to use mac drivers in linux.
but I see in the description for libsane-extras (v. 1.0.18.5) in the [feisty repo]("http://packages.ubuntu.com/feisty/libs/libsane-extras") that it supports your scanner:
> hp3900 (HP ScanJet 3970C, HP ScanJet 4070, HP ScanJet 4370)I would guess you are better off if you try to download the .deb and install it.
If you use edgy it seems like you would also need to update libc6 (also available in the [feisty repo]("http://packages.ubuntu.com/feisty/base/libc6")).

---

