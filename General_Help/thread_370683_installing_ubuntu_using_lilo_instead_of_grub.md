---
title: "installing ubuntu using lilo instead of grub?"
date: 2007-02-26
forum: General Help
---

### Post by tawniteamo on 2007-02-26
is it at all possible to install ubuntu from the desktop cd using lilo instead of grub? I seem to have way too many problems with grub and lilo works like a charm every time. I know that it is possible to install lilo using the alternate cd, but I have had very little luck with the alternate.

---

### Post by crossedout on 2007-02-26
Try reading over [[COLOR="DarkOrange"]this[/COLOR]]("http://users.bigpond.net.au/hermanzone/") site.

I believe you must use the Alternate CD to accomplish what you are asking.

-Xout

---

### Post by tawniteamo on 2007-02-27
Fixed it myself. I had to manually edit the partition table and put both my root and swap inside an extended partition, now it works fine.

---

