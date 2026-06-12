---
title: "Installing a rpm package on ubuntu"
date: 2007-02-01
forum: General Help
---

### Post by rucadulu on 2007-02-01
I need to install Oracle Developer Suite 10g on my Ubuntu 6.06LTS client this package was made for Red Hat Server, does anyone have any idea how to install a rpm on Ubuntu ?

Thanks Rucadulu

---

### Post by taurus on 2007-02-01
From a terminal, do

```
sudo aptitude update
sudo aptitude install alien
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```

---

