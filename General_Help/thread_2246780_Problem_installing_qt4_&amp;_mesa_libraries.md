---
title: "Problem installing qt4 &amp; mesa libraries"
date: 2014-10-03
forum: General Help
---

### Post by el_chamb on 2014-10-03
I'm attempting to install some qt4 and mesa libraries 
```
sudo apt-get install libqt4-opengl-dev libgl1-mesa-dev
```
and receive the following error.
```
The following packages have unmet dependencies. libgl1-mesa-dev : Depends: libgl1-mesa-glx (= 10.1.0-4ubuntu5) but 10.1.3-0ubuntu0.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```
I'm running ubuntu 14.04 LTS (64 bit)

Thanks.

---

### Post by ibjsb4 on 2014-10-03
You have marked your thread solved; is it?

Check to see if libgl1-mesa-dev is version 10.1.3.

It sounds like its trying to install the non-updated version.

[http://packages.ubuntu.com/trusty/libgl1-mesa-dev](http://packages.ubuntu.com/trusty/libgl1-mesa-dev)

[http://packages.ubuntu.com/trusty-updates/libgl1-mesa-glx](http://packages.ubuntu.com/trusty-updates/libgl1-mesa-glx)

---

