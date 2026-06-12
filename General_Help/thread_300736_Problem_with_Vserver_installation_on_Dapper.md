---
title: "Problem with Vserver installation on Dapper"
date: 2006-11-16
forum: General Help
---

### Post by shufla on 2006-11-16
Hello,

I've used wiki page [https://help.ubuntu.com/community/VServer](https://help.ubuntu.com/community/VServer) to install vserver kernel in dapper. This is my sources list:
```

deb http://pl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://pl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://pl.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb      http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/  dapper uniklu-vserver

```

On VServer wikipage it's said:

```
apt-get install linux-image-2.6.15-(dapper_abi+1)-686
```

I'm using server kernel, so I've changed -686 to -server. To find dapper_abi I used command:
```

dpkg -l | egrep "linux.*server"
ii  linux-image-2.6.15-27-server 2.6.15-27.48              Linux kernel image for version 2.6.15 on Ser
ii  linux-image-server           2.6.15.25                 Linux kernel image on Server Equipment.
ii  linux-server                 2.6.15.25                 Complete Linux kernel on Server Equipment.

```

So I've tried to install vserver enabled kernel by:
```
apt-get install linux-image-2.6.15-28-server
```
w/o success, there's no package, maybe 686:
```
apt-get install linux-image-2.6.15-28-686
```

Same problem. Well, I'm able to download package by hand and install it with **dpkg -i**, but than any update from ubuntu will overriede that one. Any suggestion? Or it's a bug of vserver team?

Thanks in advance,
Luke

---

