---
title: "apt-build-ing packages"
date: 2007-05-24
forum: General Help
---

### Post by geekphreak on 2007-05-24
If I do an apt-build of a package that is already installed, will that have any impact or is apt-build only supposed to be used for packages that are not installed previously? For example, if Firefox is already installed, and I apt-build it, will the next time I start Firefox the optimized version be used?
Thanks!

---

### Post by kuja on 2007-05-24
With all likelyhood it builds a package. Installing that package would remove the current one and install the apt-builded one in its place. I've not played with apt-build before, but I'm pretty sure that's how it would behave.

---

