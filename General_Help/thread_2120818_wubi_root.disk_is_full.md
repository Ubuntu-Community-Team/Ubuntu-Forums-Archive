---
title: "wubi root.disk is full"
date: 2013-02-27
forum: General Help
---

### Post by gabilow on 2013-02-27
i have ubuntu 11.10 through wubi.
 i use it to program in php my php code has recursive function that somehow got into loop and loop 0 in root.disk became full.
i cant resize root.disk because it alrady in the maximum size, i found in the lampp folder a log file size 18G i deleted it but still loop 0 is full

---

### Post by Frogs Hair on 2013-02-27
Hello and Welcome

Re-sizing as well as moving a Wubi installation to a partition is covered at the link. A 30 GB max can be set manually during installation other wise the installer defaults to given size .      [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by fdrake on 2013-02-27
> **gabilow said:**
> i have ubuntu 11.10 through wubi.
 i use it to program in php my php code has recursive function that somehow got into loop and loop 0 in root.disk became full.
i cant resize root.disk because it alrady in the maximum size, i found in the lampp folder a log file size 18G i deleted it but still loop 0 is full
use grub and login into recovery mode >> root, and type
```

mount -o rw,remount /

```
disable the php scripts (mov the /etc/www folder into another place so that the function won't run)

also check the size with df du, check the /tmp /var folders for possible big log files.

---

