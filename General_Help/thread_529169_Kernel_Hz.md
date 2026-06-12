---
title: "Kernel Hz"
date: 2007-08-18
forum: General Help
---

### Post by Dudsmacka2 on 2007-08-18
On a default 7.04 server edition install what is the value for the kernel timeslice time (hz)?

---

### Post by gmaniac on 2007-08-18
I don't know, but you could find out by
```
cat /boot/config-`uname -r` | grep '^CONFIG_HZ='
```

---

