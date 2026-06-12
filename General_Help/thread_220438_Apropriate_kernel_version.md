---
title: "Apropriate kernel version"
date: 2006-07-21
forum: General Help
---

### Post by jis on 2006-07-21
"uname -r" command shows that my kernel version is 2.6.15-23-386. I have installed xubuntu on PIII computer so why the version does not end by 686 instead of 386? Does the 686 version have some advantage over 386 version?

---

### Post by PriceChild on 2006-07-21
you have to install the 686 version yourself.... for example```
sudo aptitude install linux-image-686
```is a metapackage that will ensure you continue to keep the new 686 optimised kernels.

There's meant to be an improvement, but nothing to significant.

---

