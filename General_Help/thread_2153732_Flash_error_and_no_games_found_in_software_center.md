---
title: "Flash error and no games found in software center"
date: 2013-06-12
forum: General Help
---

### Post by phelenon on 2013-06-12
I installed Lubuntu today.It is fast,but when i try to install flash it took me to the adobe site which offered no help.I tried installing chrome and there was an error in dependancy.
I also found no games in software center except cards and a poker game

---

### Post by slickymaster on 2013-06-12
> **phelenon said:**
> I installed Lubuntu today.It is fast,but when i try to install flash it took me to the adobe site which offered no help...
The correct way to install Adobe Flash Player is to use the repositories. Search for "flash plug-in" in Ubuntu Software Center, and then install it from there.
Or run this command:```
sudo apt-get install flashplugin-nonfree
```

> **phelenon said:**
> ... I tried installing chrome and there was an error in dependancy...
If you're getting this dependency error:```
"Error: Dependency is not satisfiable: libudev0 (>=147)"
```all you have to do is to grab libudev0 which is absent from 13.04's repository. Download and install libudev0 from here:
[libudev0 for 32bit]("https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325790/+files/libudev0_175-0ubuntu19_i386.deb")
[libudev0 for 64bit]("https://launchpad.net/ubuntu/+source/udev/175-0ubuntu19/+build/4325788/+files/libudev0_175-0ubuntu19_amd64.deb")
But I must say that it's odd if you're getting that dependency issue, since Chrome 27 has the fix for the missing dependency.

---

### Post by gordintoronto on 2013-06-12
The other simple way to get Flash -- and lots of other useful stuff -- is to install lubuntu-restricted-extras.

---

### Post by Rex Bouwense on 2013-06-12
> **phelenon said:**
> I installed Lubuntu today....
I also found no games in software center except cards and a poker game
If you open up the Lubuntu Software Center you will find dozens of games to download, install, and pass the time away.

---

