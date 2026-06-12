---
title: "Updater?"
date: 2019-01-07
forum: General Help
---

### Post by Daveski17 on 2019-01-07
I haven’t had an update for Ubuntu 16.04 LTS for a few days.  In settings the ‘up to date’ has changed to ‘Install Updates’.

[ATTACH=CONFIG]282115[/ATTACH]

Yet when I click on this I am informed I am up to date. Does anyone know what’s going on with this?

Thanks.

---

### Post by #&amp;thj^% on 2019-01-07
Dose anything look unusual with:
```
sudo apt-get update
```
But i also have very few available updates lately. (This is normal at times)

---

### Post by Daveski17 on 2019-01-07
Thanks for your reply. I just got this:

Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Fetched 323 kB in 0s (360 kB/s)                               
Reading package lists... Done

---

### Post by #&amp;thj^% on 2019-01-07
yep that all looks ok to me.
My latest updates look like this:
```
2019-01-07 08:21:32 install linux-headers-5.0.0-050000rc1:all <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:22 install linux-headers-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:29 install linux-image-unsigned-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:32 install linux-modules-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:57:00 install gvfs-bin:amd64 <none> 1.36.1-0ubuntu1.2
2019-01-07 09:22:28 install lynis:all <none> 2.7.0-100
2019-01-07 09:27:02 install lynis:all 2.7.0-100 2.7.0-100

```
And i installed those myself <in other words nothing to see here>

---

### Post by maglin2 on 2019-01-07
No updates here either for a few days - until today when psmisc was updated.

/var/log/apt shows last update before that was tzdata on 01/01/19

(but then this is kubuntu 18.04, not ubuntu 16.04)

---

### Post by Daveski17 on 2019-01-07
> **1fallen said:**
> yep that all looks ok to me.
My latest updates look like this:
```
2019-01-07 08:21:32 install linux-headers-5.0.0-050000rc1:all <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:22 install linux-headers-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:29 install linux-image-unsigned-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:22:32 install linux-modules-5.0.0-050000rc1-lowlatency:amd64 <none> 5.0.0-050000rc1.201901062130
2019-01-07 08:57:00 install gvfs-bin:amd64 <none> 1.36.1-0ubuntu1.2
2019-01-07 09:22:28 install lynis:all <none> 2.7.0-100
2019-01-07 09:27:02 install lynis:all 2.7.0-100 2.7.0-100

```
And i installed those myself <in other words nothing to see here>

OK thanks.

---

### Post by Daveski17 on 2019-01-07
> **maglin2 said:**
> No updates here either for a few days - until today when psmisc was updated.

/var/log/apt shows last update before that was tzdata on 01/01/19

(but then this is kubuntu 18.04, not ubuntu 16.04)

Thanks.

---

### Post by Daveski17 on 2019-01-08
I had an update today, everything seems fine.

[ATTACH=CONFIG]282131[/ATTACH]

---

