---
title: "reinstall zlib on ubuntu 12.04"
date: 2015-04-14
forum: General Help
---

### Post by associates on 2015-04-14
Hi,

Is there a way to check the version of zlib installed on my ubuntu server 12.04.5 32bit.

I'd like to update it to zlib-1.2.8 (the most current version at the time of posting this question).

So far what I have installed on my system is zlib1g, zlib1g-dev, libcompress-raw-zlib-perl, libcompress-zlib-perl, libio-compress-zlib-per, libio-zlib-perl. Do I need to uninstalll all of these first before installing zlib-1.2.8.

Any help is greatly appreciated

---

### Post by dino99 on 2015-04-14
[http://askubuntu.com/questions/162133/find-version-of-development-library-from-command-line](http://askubuntu.com/questions/162133/find-version-of-development-library-from-command-line)

take in mind that introducing a non genuine version of a lib/app/package can break the whole system, due to strict dependecies version of some packages, and/or new feature/renamed feature/...

---

