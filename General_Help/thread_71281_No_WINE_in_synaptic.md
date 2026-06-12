---
title: "No WINE in synaptic"
date: 2005-10-02
forum: General Help
---

### Post by nighttime on 2005-10-02
I was about to install WINE, when I pushed the "apply" button it gave me some error and refreshed the list of packages, and then there were a lot of them (including WINE) missing from the list... I think this might have to do with the fact that I changed my sources.list file before pressing "Apply", and I made no backup... any help, please?

---

### Post by aysiu on 2005-10-07
Have you tried following the instructions at

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

?

Just delete the lines about the backports.
```
sudo apt-get update
sudo apt-get install wine
```

---

