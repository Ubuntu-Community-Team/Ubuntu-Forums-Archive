---
title: "twinkle-1.4.2 on 13.10"
date: 2014-01-05
forum: General Help
---

### Post by rmstock2 on 2014-01-05
I adapted twinkle-1.4.2 to run on ubuntu 13.10 :

[http://crashrecovery.org/twinkle/ubuntu1310/]("http://crashrecovery.org/twinkle/ubuntu1210/")

To install twinkle_1.4.2-2.2_amd64.deb on ubuntu 13.10 one needs an
additional package libqt3-mt, which is not included anymore by default
with Ubuntu 13.10.

( There is however a free drop-in replacement available from
  [http://trolltech.com](http://trolltech.com) which is called qt-x11-free by the ubuntu
  people. The original source package was retrieved from lanchpad at
  [https://launchpad.net/ubuntu/+source/qt-x11-free](https://launchpad.net/ubuntu/+source/qt-x11-free) .  I built it on
  ubuntu 13.10 amd64 which is for download at
  [ftp://ftp.crashrecovery.org/pub/linux/qt3/ubuntu1310/](ftp://ftp.crashrecovery.org/pub/linux/qt3/ubuntu1310/) )

So first install libqt3-mt_3.3.8-b-8ubuntu3_amd64.deb, which i also
included in this directory, and next twinkle_1.4.2-2.2_amd64.deb can be
installed.

```

total 7260
-rw-r--r-- 1 root root 3278220 Jan  5 23:55 libqt3-mt_3.3.8-b-8ubuntu3_amd64.deb
-rw-r--r-- 1 root root     604 Jan  6 02:52 MD5SUM
-rw-r--r-- 1 root root     692 Jan  6 02:11 README.twinkle
-rw-r--r-- 1 root root  174935 Jan  6 00:30 twinkle_1.4.2-2.2_amd64.build
-rw-r--r-- 1 root root    1644 Jan  6 00:30 twinkle_1.4.2-2.2_amd64.changes
-rw-r--r-- 1 root root 1677910 Jan  6 00:30 twinkle_1.4.2-2.2_amd64.deb
-rw-r--r-- 1 root root  132310 Jan  6 00:16 twinkle_1.4.2-2.2.diff.gz
-rw-r--r-- 1 root root    1555 Jan  6 00:16 twinkle_1.4.2-2.2.dsc
-rw-r--r-- 1 root root 1601100 Jan  5 23:00 twinkle_1.4.2.orig.tar.gz
-rw-r--r-- 1 root root  320236 Jan  6 02:09 twinkle-ubuntu1310.jpg
-rw-r--r-- 1 root root  219465 Jan  6 02:51 twinkle-ubuntu1310-s.jpg
```

```

58476edff4ad9b4a3bb2d7ae2b0e3494  libqt3-mt_3.3.8-b-8ubuntu3_amd64.deb
0930efe000c1727fc67c70727e030c1c  README.twinkle
55531f96c78089cbdebb7d3d9b424c1a  twinkle_1.4.2-2.2_amd64.build
b3329d2d0d98e4c304a40aa19dca056e  twinkle_1.4.2-2.2_amd64.changes
5cab4408eeced40d0bc7ada28d936edf  twinkle_1.4.2-2.2_amd64.deb
1065922d708395c6601761eb3ab3d496  twinkle_1.4.2-2.2.diff.gz
e97c273695197375c8ae2cf005443af3  twinkle_1.4.2-2.2.dsc
d70c8972f296ffd998c7fb698774705b  twinkle_1.4.2.orig.tar.gz
537531d45c7b20abc3c8b0b213bdea20  twinkle-ubuntu1310.jpg
bc50d198b8397b853016469761718472  twinkle-ubuntu1310-s.jpg
```

[IMG]http://crashrecovery.org/twinkle/ubuntu1310/twinkle-ubuntu1310-s.jpg[/IMG]

---

### Post by rmstock2 on 2014-01-05
whats up with this forum software ? Here is the correct link :[URL="http://crashrecovery.org/twinkle/ubuntu1310/"]

http://crashrecovery.org/twinkle/ubuntu1310/[/URL]

---

### Post by haer on 2014-04-22
Seriously dude.. You rock! :)

---

