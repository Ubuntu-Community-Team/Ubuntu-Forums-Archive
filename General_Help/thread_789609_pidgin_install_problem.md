---
title: "pidgin install problem"
date: 2008-05-10
forum: General Help
---

### Post by goli123 on 2008-05-10
im trying to install pidgin on my computer but every time after i "make" 
it seem to be installing but in the end i get this: 
```
make[3]: Leaving directory `/home/goli123/pidgin'
make[2]: Leaving directory `/home/goli123/pidgin'
Making all in m4macros
make[2]: Entering directory `/home/goli123/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/goli123/m4macros'
Making all in po
make[2]: Entering directory `/home/goli123/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/goli123/po'
Making all in share/ca-certs
make[2]: Entering directory `/home/goli123/share/ca-certs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/goli123/share/ca-certs'
Making all in share/sounds
make[2]: Entering directory `/home/goli123/share/sounds'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/goli123/share/sounds'
make[2]: Entering directory `/home/goli123'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/goli123'
make[1]: Leaving directory `/home/goli123'
```
what should i do now?

---

### Post by inportb on 2008-05-10
Why are you building Pidgin instead of installing the debs? version 2.4.1 is in the repositories.

---

### Post by goli123 on 2008-05-10
its doesnt work too because i have gaim installed. how do i remove it?

---

### Post by Sef on 2008-05-10
Gaim is the old name for pidgin.  What version of ubuntu are you using?

---

### Post by goli123 on 2008-05-11
the version is :

 
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper

---

### Post by DoktorSeven on 2008-05-11
"make" just builds the package, it does not install it.   What you're seeing is the end of the build process.

To install:
```

sudo make install

```

You can also install "checkinstall" from the repos and do
```

sudo checkinstall

```
which will build a package and install it so you can manage it with apt and related Ubuntu package utilities; however, last time I attempted to use checkinstall on Pidgin failed for some odd reason (some sort of file conflict), this could be resolved now though.

---

### Post by MaindotC on 2008-05-11
Goli you really should try the world of Gutsy.

---

### Post by goli123 on 2008-05-11
thx doktor its working now! 
thx every1 else who tried to help me !

---

