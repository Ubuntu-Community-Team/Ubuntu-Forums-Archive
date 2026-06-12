---
title: "E: Malformed line 1 in source list /etc/apt/sources.list (type)"
date: 2017-11-07
forum: General Help
---

### Post by mpmckinnon on 2017-11-07
Hey there guys I would love some help if anyone can please. I am running Ubuntu 17.10 and when I run sudo apt-get update I get E: Malformed line 1 in source list /etc/apt/sources.list (type) E: The list of sources could not be read. This is what my source list looks like 

```
###### Ubuntu Main Repos

###### Ubuntu Update Repos
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner

###### Ubuntu Extras Repo
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse restricted universe main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful multiverse restricted universe main #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) artful-security multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-proposed multiverse universe main restricted
```I tried to rebuild it from what I could find on-line. I would rather be able to fix it then reinstall Ubuntu. Any help would be great help at this point.

Thank You

---

### Post by spjackson on 2017-11-07
More than likely there is a spurious, perhaps invisible, character on line 1. If the first line looks empty, then try deleting that line. Alternatively, please attach it to a post rather than pasting it.

---

