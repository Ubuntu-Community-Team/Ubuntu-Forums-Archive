---
title: "bit level flash drive copy"
date: 2007-09-18
forum: General Help
---

### Post by fusionisthefuture on 2007-09-18
is it possible to make a bit level copy of a flash drive in ubuntu with no extra software, and if not, what do i need?  

thanks,
-arne

---

### Post by McNils on 2007-09-18
Yes it is. Use **dd**.
Something like this should work. Assuming yor flash drive is /dev/sda1. The drive should not be mounted.

```

dd if=/dev/sda1 of=/tmp/dump.dd

```

---

