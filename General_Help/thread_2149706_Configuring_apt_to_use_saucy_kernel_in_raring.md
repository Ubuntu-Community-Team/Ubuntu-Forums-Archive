---
title: "Configuring apt to use saucy kernel in raring"
date: 2013-05-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-29
Added this to [FONT=courier new]/etc/apt/sources.list[/FONT]
```
deb http://us.archive.ubuntu.com/ubuntu/ saucy main
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main
```
Created [FONT=courier new]/etc/apt/preferences[/FONT] with this in it
```
Package: *
Pin: release a=saucy
Pin-Priority: -10

Package: linux-image,linux-firmware,linux-headers-generic,linux-image-generic,linux-libc-dev
Pin: release a=saucy
Pin-Priority: 700
```
It does not shows the packages as a update, i could force the upgrade in synaptic but i want it to auto update

**EDIT:**
Solution (-10 overrides it, should use 100):```
Package: *
Pin: release a=saucy
Pin-Priority: 100

Package: linux-generic,linux-firmware,linux-headers-generic,linux-image-generic,linux-libc-dev
Pin: release a=saucy
Pin-Priority: 500
```

---

### Post by ceefour2 on 2013-08-25
Thank you!! Very useful howto

---

### Post by ceefour2 on 2013-08-27
1. You should replace editing /etc/apt/sources.list with creating a file /etc/apt/sources.list.d/saucy.list
2. You should replace /etc/apt/preferences with creating a file /etc/apt/preferences.d/saucy.pref

Rather than doing a full-upgrade (which results in broken packages), I only upgraded the following packages:

1. linux-generic
2. linux-image-generic
3. linux-headers-generic
4. linux-image-extra-x.xx.x-x-generic
5. linux-firmware
6. linux-libc-dev

i.e.

[FONT=courier new]sudo aptitude install linux-generic linux-image-generic linux-headers-generic linux-firmware linux-libc-dev[/FONT]
 
After that I disabled the saucy repository again.

---

