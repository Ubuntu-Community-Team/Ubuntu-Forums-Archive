---
title: "re enable  ipv6"
date: 2008-07-03
forum: General Help
---

### Post by bu2971x on 2008-07-03
this is the official way to turn OFF  ipv6- in 8.04

sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases

what is the official way to turn it back on  ??  thanks

---

### Post by sisco311 on 2008-07-03
First backup your file:
```
sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases-backup
```then try:
```
 sudo sed -i -e 's/#&\nalias net-pf-10 off/alias net-pf-10 ipv6/' /etc/modprobe.d/aliases
```
or
```
sudo sed -i -e 's/alias net-pf-10 off/alias net-pf-10 ipv6/' /etc/modprobe.d/aliases
```

---

