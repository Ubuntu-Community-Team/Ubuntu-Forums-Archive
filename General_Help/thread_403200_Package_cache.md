---
title: "Package cache"
date: 2007-04-06
forum: General Help
---

### Post by thai84 on 2007-04-06
"...When you ask apt to install a software package, it downloads the package and stores it in a cache on your disk before it does the actual installation. If you then remove the package but later change your mind again and reinstall it, apt doesn't need to fetch it from the Internet again because the package is sitting in the local cache..."
   Please tell me where the package cache is.

---

### Post by zvacet on 2007-04-06
**var/cache/apt/archives**

---

### Post by jaka on 2007-04-20
> **zvacet said:**
> **var/cache/apt/archives**

How to delete all deb packages in **var/cache/apt/archives? **

---

### Post by tactus on 2007-04-20
sudo apt-get clean

---

