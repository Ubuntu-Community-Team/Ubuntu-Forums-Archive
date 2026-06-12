---
title: "mounting with noauto"
date: 2007-05-29
forum: General Help
---

### Post by sanoj on 2007-05-29
When the following entry is in my /etc/fstab,

```
/dev/hdb1 /media/backup   ext3    data=journal,noauto,user        0       2
```

it still mounts the device at boot-time. I would expect the "noauto" flag to disable this. How do I solve this problem?

---

