---
title: "Ubuntu 7.04 Crashed"
date: 2007-07-31
forum: General Help
---

### Post by dashten on 2007-07-31
I was reading a tutorial on how to install Beryl and after I finished following the tutorial I rebooted and Ubuntu wouldn't load it would just show:
input3, status -32
drivers/usb/input/hid-core.c: can't reset device, 0000.001d.0-1
over and over again.

---

### Post by be4truth on 2007-08-02
You could boot into rescue mode and then type 

```
apt-get remove --purge beryl
```

That will remove beryl completely including the configuration files. You should be able to boot into your Feisty after.

---

