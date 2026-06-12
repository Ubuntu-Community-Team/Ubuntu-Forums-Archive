---
title: "after upgrade to 7.1o I can not access cd rom"
date: 2008-03-06
forum: General Help
---

### Post by bigdavesr on 2008-03-06
I installed 7.04 with my cdrw. Went fine. cdrw worked. Upgraded to7.10 via internet. Cd shows to be installed but when i try to use  it it dose not find it. If anyone knows a solution I would be for ever indepted. Thanks in advance.

---

### Post by dcstar on 2008-03-07
> **bigdavesr said:**
> I installed 7.04 with my cdrw. Went fine. cdrw worked. Upgraded to7.10 via internet. Cd shows to be installed but when i try to use  it it dose not find it. If anyone knows a solution I would be for ever indepted. Thanks in advance.

Post contents of the following:

```
cat /etc/fstab
ls -al /dev/cd*
```

---

