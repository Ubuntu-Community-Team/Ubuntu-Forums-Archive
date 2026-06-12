---
title: "how to enable auto- hda mounting in Ubuntu?"
date: 2005-10-27
forum: General Help
---

### Post by kazuya on 2005-10-27
How do you ensure that upon connecting of new hard drives to machine or USB drive that everything gets auto mounted and shown upon booting up Ubuntu in kde/gnome/xfce?

Any ideas guys?

---

### Post by mykey on 2005-10-27
make sure for the device supposed to get mounted automatically at boot an entry in /etc/fstab exists that looks similar to this:
```
/dev/hda9       /media/hda9    vfat     defaults   0       0

```

---

