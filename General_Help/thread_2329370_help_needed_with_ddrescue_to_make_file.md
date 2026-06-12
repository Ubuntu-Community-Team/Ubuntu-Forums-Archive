---
title: "help needed with ddrescue to make file"
date: 2016-06-30
forum: General Help
---

### Post by lance bermudez on 2016-06-30
to make 1gb file using dd
dd if=/dev/urandom of=/root/test3 bs=1M count=1048576

so how do i do that with ddrescure?

---

### Post by papibe on 2016-06-30
Hi lance bermudez.

If you want to create a 1G file of random data:
```
ddrescue -s 1Gi /dev/urandom ./test3.img
```
Hope it helps.
Regards.

---

