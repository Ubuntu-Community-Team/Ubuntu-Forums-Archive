---
title: "Ubuntu 18.04 LTS updates failing to install"
date: 2018-05-22
forum: General Help
---

### Post by techguru30 on 2018-05-22
Ubuntu 18.04 LTS updates failing to install.

---

### Post by cruzer001 on 2018-05-22
```
sudo apt -f install
```
Did you do that?

Still broke?  Please post the output of that command.

---

### Post by Cavsfan on 2018-05-22
^[COLOR=#000000]cruzer001's idea should work, if not try these:[/COLOR]

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update

```

You can use apt or apt-get, I'm still stuck on apt-get. Just my preference.

---

### Post by techguru30 on 2018-05-22
> **cruzer001 said:**
> ```
sudo apt -f install
```
Did you do that?

Still broke?  Please post the output of that command.
That fixed the issue. Thanks for your help.

---

