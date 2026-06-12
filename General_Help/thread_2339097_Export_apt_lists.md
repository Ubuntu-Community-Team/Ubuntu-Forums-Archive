---
title: "Export apt lists"
date: 2016-10-04
forum: General Help
---

### Post by mintmag on 2016-10-04
Hi there I'm trying to create a portable offline repository using dir::cache::archives and dir::state::lists

you need both the lists and the beb packages for it to work and it does. However it isn't portable. When I create a fresh install of either Ubuntu or Mint and copy the var/lib/apt/lists from the old installation it don't work. apt access the repository but doesn't know what it can and can't get because the debs haven't been indexed. How do I copy the indexed data for the deb from var/lib/apt/lists

This is the only way I wish to do this since dpkg-scannpackges doesn't work for me nor does it index packages needed for dist-upgrade like apt-get update does. I really need to a portable version of apt-get update.

---

### Post by TheFu on 2016-10-05
```
$ dpkg --get-selections
```

apt-get is slightly deprecated. Plain **apt** is recommended now.

---

