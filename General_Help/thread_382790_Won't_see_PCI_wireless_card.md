---
title: "Won't see PCI wireless card"
date: 2007-03-12
forum: General Help
---

### Post by CocoAUS on 2007-03-12
I know my wireless card works fine with Ubuntu, because I've used it before via ndiswrapper.  I recently did a reinstall, though, without the card in during the install.  I figured I would just plug it in later and be good to go, but I can't get Ubuntu to even see it.  ifconfig only shows my integrated ethernet.  How do I get Ubuntu to see this card?  Thanks.

---

### Post by strabes on 2007-03-12
I'm not sure if I know what your problem is, but what is the output of this command?

```
cat /etc/network/interfaces
```

Perhaps someone else can help you more.

---

