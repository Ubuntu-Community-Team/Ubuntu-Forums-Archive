---
title: "Apt-get via ssh"
date: 2004-11-02
forum: General Help
---

### Post by smevans on 2004-11-02
Hi

am very new to Linux and was wondering how i use apt-get to install things when connected to machine via Putty ?

Thanks

---

### Post by diebels on 2004-11-02
```
sudo apt-get update && sudo apt-get dist-upgrade
```will keep all installed packages up to date.


```
sudo apt-get install package-name
```installs single package.


```
apt-cache search parts-of-package-name
```searches for package.

Edit /etc/apt/sources.list for adding/removing repositorys

---

