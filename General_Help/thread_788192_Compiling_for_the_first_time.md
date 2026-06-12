---
title: "Compiling for the first time"
date: 2008-05-09
forum: General Help
---

### Post by moribalkin on 2008-05-09
Hey there, I'm trying to compile these 2 binary and source files ([http://www.stepmania.com/wiki/Downloads](http://www.stepmania.com/wiki/Downloads)). But the thing is I'm pretty new to this. Before you ask there is a .deb for Stepmania on Ubuntu, I know, but the thing is I can't use the 4.0 version one. So I need the 3.9

Can I get a good detailed step in compiling this?

---

### Post by Monicker on 2008-05-09
[http://monkeyblog.org/ubuntu/installing/#source]("http://monkeyblog.org/ubuntu/installing/#source")

---

### Post by gug@fnal.gov on 2008-05-09
I would recommend starting with a google search on something like "rebuild deb package". I did that and this is one of the first hits I found: [http://soniahamilton.wordpress.com/2006/11/10/rebuild-a-deb-package/](http://soniahamilton.wordpress.com/2006/11/10/rebuild-a-deb-package/)

the first part claims:
To rebuild a package, I usually:

    * apt-get source package
    * cd package
    * dch -i

This will open debian/changelog , then you can increment the package version/release/etc, put in changelog info, etc

    * dpkg-buildpackage -rfakeroot -uc -b

Disclaimer: I haver rebuilt rpms from source before but not yet found the need to do it for debs yet, so the above may not be complete or accurate.

---

