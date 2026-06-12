---
title: "ifconfig command missing from 18.04 bionic"
date: 2018-08-28
forum: General Help
---

### Post by cam17 on 2018-08-28
Has the ifconfig command been deprecated from 18.04  Bionic. After upgrading from 16.04 to 18.04 and performing an update the command was missing and I had to install it manually.

---

### Post by slickymaster on 2018-08-28
The **ifconfig** command has been deprecated because it was considered to have mediocre IPv6 support. The new alternative for examining a network configuration is the **ip** command.

If you still prefer to use ifconfig, you can easily install it as part of the net-tools package```
sudo apt install net-tools
```

---

### Post by HermanAB on 2018-08-28
On BSD, ifconfig has new features that are quite useful.  I hope that it will eventually make a proper comeback on Linux.

---

