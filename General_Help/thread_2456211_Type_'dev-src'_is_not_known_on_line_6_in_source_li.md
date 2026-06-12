---
title: "Type 'dev-src' is not known on line 6 in source list /etc/apt/sources.list"
date: 2021-01-06
forum: General Help
---

### Post by holiday2 on 2021-01-06
I don't see what's wrong. The only change I've made to the file is to comment out the cdrom line and removed the '#' before each `dev-src` entry.

```
sudo apt update: Type 'dev-src' is not known on line 6 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```


```
# deb cdrom:[Ubuntu-MATE 20.10 _Groovy Gorilla_ - Release amd64 (20201022)]/ groovy main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ groovy main restricted
dev-src http://ca.archive.ubuntu.com/ubuntu/ groovy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ groovy-updates main restricted
dev-src http://ca.archive.ubuntu.com/ubuntu/ groovy-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ groovy universe
dev-src http://ca.archive.ubuntu.com/ubuntu/ groovy universe
deb http://ca.archive.ubuntu.com/ubuntu/ groovy-updates universe
dev-src http://ca.archive.ubuntu.com/ubuntu/ groovy-updates universe

```

---

### Post by &amp;KyT$0P# on 2021-01-06
Every "dev-src" should be **deb**-src .

---

### Post by holiday2 on 2021-01-06
> **halogen2 said:**
> Every "dev-src" should be **deb**-src .

Yup. Works like a charm. 

Thanks

---

