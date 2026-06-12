---
title: "Filesystem ID summary"
date: 2007-10-17
forum: General Help
---

### Post by zkab on 2007-10-17
Is there a command that gives a summary of all filesystem ID ... I have seen it somewhere
Anyone knows ?

---

### Post by thirddeep on 2007-10-17
While someone else may know a direct command, here is the indirect way
```
sudo fdisk /dev/XXX
```

Then press "l" (small L).

Thd.

---

### Post by questpro on 2007-10-17
> **zkab said:**
> Is there a command that gives a summary of all filesystem ID ... I have seen it somewhere
Anyone knows ?

Do you mean the UUID listed in the /etc/fstab ??!!

---

