---
title: "update issue"
date: 2019-12-02
forum: General Help
---

### Post by mwieting on 2019-12-02
When i run sudo apt-get update i get the following:
```
Ign:1 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Hit:5 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) bionic InRelease
Hit:6 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) bionic InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease
Ign:9 [https://dl.bintray.com/openhab/apt-repo2](https://dl.bintray.com/openhab/apt-repo2) stable InRelease
Get:11 [https://dl.bintray.com/openhab/apt-repo2](https://dl.bintray.com/openhab/apt-repo2) stable Release [6,051 B]
Hit:12 [http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu](http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu) bionic InRelease
Hit:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security InRelease
Fetched 6,051 B in 2s (2,869 B/s)
Reading package lists... Done
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Contents-deb (contrib/Contents-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Contents-deb (contrib/Contents-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (contrib/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Packages (contrib/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (contrib/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Translations (contrib/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Contents-deb (contrib/Contents-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target Contents-deb (contrib/Contents-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (contrib/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
W: Target CNF (contrib/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:10
```

---

### Post by deadflowr on 2019-12-02
You have duplicate lines in your sources.list.
post back the sources.list file
```
cat /etc/apt/sources.list
```
to see which are the same.

---

