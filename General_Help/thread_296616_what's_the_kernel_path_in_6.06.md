---
title: "what's the kernel path in 6.06?"
date: 2006-11-09
forum: General Help
---

### Post by sanyamoy on 2006-11-09
It used to be /usr/src/,but I found nothing there.
what is its exactly path?I'm green with this os...

---

### Post by jpeddicord on 2006-11-09
You must install the package kernel-headers if you wish to have the sources in /usr/src.
```
sudo apt-get install kernel-headers
```

Jacob

---

### Post by sanyamoy on 2006-11-09
actually,I want to learn how to program as kernel model,does this method work?
ps.my kernel version is 2.6.15-27-k7,and the header's version is kernel-headers-2.4.27-2-k7 2.4.27-12,is it all right?
thank u...

---

