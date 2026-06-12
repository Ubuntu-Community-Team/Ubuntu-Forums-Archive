---
title: "sudo apt-get purge rabbitvcs"
date: 2012-11-07
forum: General Help
---

### Post by purencool on 2012-11-07
Hi ubuntu people,

I am trying to remove rabbitvcs from ubuntu 12.04 but I 
keep getting this issue below can anyone tell what it means.

sudo apt-get purge rabbitvcs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'rabbitvcs' can't be removed

Thanks

---

### Post by oldos2er on 2012-11-08
You need to specify which rabbitvcs-* package, or just list all of them ```
sudo apt-get purge rabbitvcs-cli rabbitvcs-core rabbitvcs-gedit rabbitvcs-nautilus
```

A virtual package is a package that doesn't really exist: [http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg](http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg)

---

