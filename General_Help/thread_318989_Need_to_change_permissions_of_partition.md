---
title: "Need to change permissions of partition"
date: 2006-12-14
forum: General Help
---

### Post by bogey on 2006-12-14
I have a partition on my hard drive that I want to be able to read and write to.  Currently the permissions are set to root.  How do I change the permissions to allow me to read and write to it ?


It is mounted and this is the line from my FSTAB.

# /dev/sdb3
UUID=abb93d84-e28e-4d0c-b02c-927635bc757d /media/sdb3     ext3    defaults        0       2

---

### Post by aysiu on 2006-12-14
This should help: ```
sudo chown -R bogey:bogey /media/sdb3
sudo chmod -R 755 /media/sdb3
```

---

