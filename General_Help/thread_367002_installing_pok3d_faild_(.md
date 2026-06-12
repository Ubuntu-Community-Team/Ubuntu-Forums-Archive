---
title: "installing pok3d faild :("
date: 2007-02-21
forum: General Help
---

### Post by sharperguy on 2007-02-21
I tried to install pok3d becasue it looks really good

On the website it says to install on edgy:
```

Add the following lines to your /etc/apt/sources.list 

deb http://pok3d.net/edgy ./
deb-src http://pok3d.net/edgy ./
deb http://pok3d.net/edgy-non-free ./

If not present, add
deb http://archive.ubuntu.com/ubuntu/ edgy universe 

Install the software and the graphics: 

apt-get update
apt-get install python-poker3d pok3d-data Run with /usr/games/poker3d

```

I did that and i get this error on installing the last package:
```

Unpacking poker3d-data (from .../poker3d-data_1.1.29-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/poker3d-data_1.1.29-1_all.deb (--unpack):
 trying to overwrite `/usr/share/poker3d/data/PLACEHOLDER', which is also in package python-poker3d
Errors were encountered while processing:
 /var/cache/apt/archives/poker3d-data_1.1.29-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:(:(

Can anyone help?

---

### Post by sharperguy on 2007-02-23
Ok I got it to install

Now I need zope.interface which for some reason didn't get installed as a dependancy


However I don't know which package I need

I tried zope3 and zope-common but no luck

It's somthing to do with python

---

