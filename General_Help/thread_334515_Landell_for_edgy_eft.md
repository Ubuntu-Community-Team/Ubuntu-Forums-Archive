---
title: "Landell for edgy eft"
date: 2007-01-09
forum: General Help
---

### Post by tarun86 on 2007-01-09
Hii

Have anyone been successful in installing Landell or Tapioca on his/her Eft machine?? If yes can ..may be you can give some idea about it!! I tried source compilation but ended up with lots of errors both with Landell n tapioca.

Is there any repo for edgy eft having landell ?? like dapper has one *deb [http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt) dapper main*

thanks :)

---

### Post by surhudm on 2007-01-13
I am also trying to install landell on kubuntu edgy...

But the apt-get says no package called landell found.

Then I tried to compile the package using the source. But it say /lib/cpp fails sanity test. When I went to the config.log of the file I see:

conftest.c:11:20: error: stdarg.h: No such file or directory
In file included from conftest.c:12:
/usr/include/stdio.h:34:21: error: stddef.h: No such file or directory

This is surprising since I have installed the gcc libraries required. I have the stdarg.h file but it seems that the comiler is not able to find it. Maybe there is a problem that the libraries are not linked. Any help would be appreciated.

Surhud

---

### Post by arbos on 2007-01-14
Read this [http://linux-facile.blogspot.com/2006/12/appelez-en-voip-avec-tapioca.html]("http://linux-facile.blogspot.com/2006/12/appelez-en-voip-avec-tapioca.html")

---

### Post by surhudm on 2007-01-21
Hi,

I checked that link but my problem is that I cannot use http_proxy from tapiocaui so was trying to install landell...

S

---

### Post by sovereign_soul on 2007-02-28
a deb package is available from the same website. However, even though it gets install without any errors, whenever run it reports an error.

Do check it anyway.

---

