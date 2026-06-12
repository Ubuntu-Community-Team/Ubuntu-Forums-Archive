---
title: "wtf happened to my display"
date: 2008-02-14
forum: General Help
---

### Post by wtfdoyouwantdude on 2008-02-14
umm i change my grapics driver from the default to the intel 945 driver and all hell broke loose. now i cant boot into my system. it goes as far as loading everything then gives me "kinit: no resume image, doing normal boot" and ask for a login name and password. how do i fix this without reinstalling everything.  :mad:

---

### Post by NT4usB on 2008-02-14
log in and type:```
sudo dpkg-reconfigure -phigh xserver-xorg
```[More reading.]("http://users.bigpond.net.au/hermanzone/p7.html")

---

### Post by wtfdoyouwantdude on 2008-02-14
thank you very much. i needed that help badly. bone head move, but i was hoping by using the other driver it would get my video out working better.

---

