---
title: "Ubuntu source code (not programs)"
date: 2013-08-11
forum: General Help
---

### Post by startas on 2013-08-11
Is ubuntu source code available somewhere ? I mean real source code, scripts, which are used to build packages from source code, i.e., arch linux uses pkgbuild files, which has information like :
1) url, from where to download programs source code,
2) programs dependencies, conflicts,
3) programs compilation configuration, like "./configure --enable-some features; make"
4) installation locations.
I'm wondering if there is available ubuntu's equalent source code.

---

### Post by deadflowr on 2013-08-11
By default, everything that ships with Ubuntu must have the source code available.
The main repository includes source by default.
If you look at the source list, the repos listed with src are the source codes.
Just run
```
apt-get source <package>
```

This might help more
[http://askubuntu.com/questions/28372/how-do-i-get-the-source-code-of-packages-installed-through-apt-get](http://askubuntu.com/questions/28372/how-do-i-get-the-source-code-of-packages-installed-through-apt-get)

---

### Post by startas on 2013-08-11
Oh, now i see, all the scripts are inside programs source code in debian/. Thanks.

---

