---
title: "updating error 7.04 to 7.10"
date: 2007-10-28
forum: General Help
---

### Post by adolfofoliaco on 2007-10-28
Hello

I have this error when I trying to upgrade my version of ubuntu

this is the error

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/main/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/restricted/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/universe/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/multiverse/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu]/dists/feisty/multiverse/binary-i386/Packages.gz) 404 Not Found

thanks

---

### Post by ThrobbingBrain66 on 2007-10-28
Could you please post the contents of your sources.list?  We have to comment out some repositories.
```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2007-10-28
```
gksudo gedit /etc/apt/sources.list
```

put # sign in front of that lines.Save and close.

```
sudo aptitude update
```

---

### Post by adolfofoliaco on 2007-10-31
thank fix already

---

