---
title: "error: zlib not installed; cannot continue."
date: 2007-02-21
forum: General Help
---

### Post by Ted_Smith on 2007-02-21
Hi. I am trying to install an app. It says "To install type ./configure && make && make install" which I have done. However, it stops after a while and says "configure: error: zlib not installed; cannot continue.". I have tried "sudo apt-get install zlib" but it does not exist. Visited packages site ([http://packages.ubuntu.com/dapper/source/zlib](http://packages.ubuntu.com/dapper/source/zlib)) but no 'zlib' is mentioned specifically, so I tried zlib1g for which my system reported that it was already installed? 

Any ideas as to how I configure things so as to complete the install? Thanks

Ted

---

### Post by schilcha on 2007-02-21
zlib1g is ok, but for compilation you also need the development package: zlib1g-dev.
```
sudo apt-get install zlib1g-dev
```
good luck!

---

### Post by Ted_Smith on 2007-02-21
Thanks a lot...yes, that has worked now. :-)

---

