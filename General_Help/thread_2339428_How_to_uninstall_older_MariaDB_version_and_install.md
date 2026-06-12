---
title: "How to uninstall older MariaDB version and install newer?"
date: 2016-10-08
forum: General Help
---

### Post by tonma on 2016-10-08
Currently I have MariaDB 10.0 but I want to upgrade to 10.1, I followed the directions on their website:

```
sudo apt-get install software-properties-common
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8
sudo add-apt-repository 'deb [arch=amd64,i386,ppc64el] [http://mirrors.neusoft.edu.cn/mariadb/repo/10.1/ubuntu](http://mirrors.neusoft.edu.cn/mariadb/repo/10.1/ubuntu) xenial main'
sudo apt update
sudo apt install mariadb-server


```

but now I get a message saying: mariadb-server is already the newest version (10.0.27-0ubuntu0.16.04.1).
How do I remove it completely? On Synpatic I see alot of packages when I type mariadb, so I don't know which one to choose or just do a sudo purge / remove via terminal ?

Ty

---

### Post by howefield on 2016-10-08
So what is the output of 

```
apt-cache policy mariadb-server
```

---

