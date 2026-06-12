---
title: "Cant install phpmyadmin"
date: 2016-01-09
forum: General Help
---

### Post by jakr2 on 2016-01-09
sudo apt-get install phpmyadmin
I get
 ```

Reading package lists... Done
Building dependency tree
Reading state information... Done
phpmyadmin is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 8 not to upgrade.

```
But I haven't got it installed because I never have installed it.

---

### Post by QIII on 2016-01-09
What flavor and release are you using?

---

### Post by jakr2 on 2016-01-09
```
DISTRIB_ID=UbuntuDISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
```

Edit: Okay I've managed to at least install phpmyadmin but I cant get past the configuration 
```
 An error occurred while installing the database:                                                               &#9474; &#9474;                                                                                                                &#9474;
 &#9474; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)     
```

And yes im using the right password 100% certain.

---

