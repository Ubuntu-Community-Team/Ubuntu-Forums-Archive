---
title: "Force apt to reinstall a package's etc files"
date: 2007-11-12
forum: General Help
---

### Post by Stephen-I-M on 2007-11-12
I installed python-moinmoin and ran "apt-get --purge remove python-moinmoin". I deleted /etc/moin by hand.

When I reinstall the package ("sudo apt-get install python-moinmoin"), I still get:

$ ls /etc/moin
ls: /etc/moin: No such file or directory

Anyone know how to get my /etc/moin directory back? Thanks.

Stephen

---

### Post by taurus on 2007-11-12
```
sudo mkdir /etc/moin
```

---

### Post by Stephen-I-M on 2007-11-12
Whoopsie. The etc files were actually in moinmoin-common, not python-moinmoin. Doing a complete removal and reinstallation of both fixed it.

Stephen

---

