---
title: "Ubuntu not detecting HP Pavilion fingerprint reader"
date: 2021-11-05
forum: General Help
---

### Post by reimeytal on 2021-11-05
I just installed the latest LTS version of ubuntu on my HP Pavilion laptop, and would like to use my fingerprint scanner to log in. Unfortunately, ubuntu doesn't seem to automatically recognize my fingerprint scanner. How can I make ubuntu detect my fingerprint reader?


Output of ```lsusb```:
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f3:0c00 Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 002: ID 04f2:b735 Chicony Electronics Co., Ltd HP Wide Vision HD Camera
Bus 003 Device 004: ID 8087:0aaa Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by GhX6GZMB on 2021-11-05
I'm running HP as well, but must admit that the fingerprint sensor was always of no interest to me.
AFAIK, the fingerprint sensor is not really supported, I believe due to proprietary drivers and fingerprint algorithms that are not freely available.

Note that a fingerprint is useless as password, but can be used for username.

---

