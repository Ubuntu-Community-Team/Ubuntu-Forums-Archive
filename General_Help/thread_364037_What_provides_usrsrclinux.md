---
title: "What provides /usr/src/linux"
date: 2007-02-17
forum: General Help
---

### Post by kiplingw on 2007-02-17
I have searched all over the place, including the Ubuntu package website, and I cannot seem to find the package that provides /usr/src/linux. I am trying to build a driver and it complains about the missing path. 

Any ideas?

Kip

---

### Post by llamakc on 2007-02-17
Typically /usr/src/linux is a symlink to the kernel-source inside of /usr/src.

---

### Post by kiplingw on 2007-02-17
On Feisty I never had to create it. Is there a package that does it automatically? Or should I create it myself?

Kip

---

### Post by llamakc on 2007-02-17
Yeah, if you have a source tree inside of /usr/src that corresponds to your running kernel (or the one you are building the module for) you can symlink it yourself.

---

### Post by kiplingw on 2007-02-17
Great. Thanks.

Kip

---

### Post by bettlebrox on 2007-02-17
Try installing the linux-headers package that correspond to the kernel your running.

---

### Post by kiplingw on 2007-02-17
Thanks. Done.

Kip

---

