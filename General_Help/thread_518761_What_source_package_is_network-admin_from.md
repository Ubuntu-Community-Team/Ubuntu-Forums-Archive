---
title: "What source package is network-admin from?"
date: 2007-08-06
forum: General Help
---

### Post by alecjw on 2007-08-06
What source package is network-admin (see below screenshot) from?

[[img=http://img360.imageshack.us/img360/193/screenshotnetworksettinzm5.th.png]](http://img360.imageshack.us/my.php?image=screenshotnetworksettinzm5.png)

Cheers =]

---

### Post by tors on 2007-08-06
```
dpkg -S network-admin
```

(for me, xubuntu-system-tools: /usr/bin/network-admin)

---

### Post by Kralizec on 2007-08-06
According to Synaptic, it resides within the 'gnome-system-tools' package.

---

### Post by alecjw on 2007-08-06
Cheers =] worked great

---

