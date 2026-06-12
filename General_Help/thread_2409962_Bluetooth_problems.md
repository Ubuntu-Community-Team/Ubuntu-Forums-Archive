---
title: "Bluetooth problems"
date: 2019-01-09
forum: General Help
---

### Post by stefano9210 on 2019-01-09
Hello,
I write because the bluetooth on my PC doesn't work correctly. Indeed, sometimes it works and sometimes not. One example, if I'm lucky and bluetooth works and after I turn it off, I can't get on again if I don't restart the PC. 

I have an ASUS K55V and Ubuntu 18.04.1 LTS

---

### Post by stefano9210 on 2019-01-10
Up

---

### Post by stefano9210 on 2019-01-11
up

---

### Post by jeremy31 on 2019-01-11
Post results for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

