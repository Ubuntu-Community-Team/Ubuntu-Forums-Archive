---
title: "can't install libgtkdev or libpangodev"
date: 2007-01-31
forum: General Help
---

### Post by jaybee99 on 2007-01-31
I am using dapper and trying to build some code that depends on gtk, cairo, pango etc. When I try to install libgtk2.0-dev with synaptic I get:

libgtk2.0-dev:
  Depends: libgtk2.0-0 (=2.8.17-1ubuntu5) but 2.8.20-0ubuntu1 is to be installed
 Depends: libpango1.0-dev but it is not going to be installed

If I try to install pango-dev I get:

libpango1.0-dev:
  Depends: libpango1.0-0 (=1.12.2-0ubuntu3) but 1.12.3-0ubuntu3 is to be installed

So I suppose I need to downgrade libgtk to v 2.8.17-1ubuntu5 and pango to 1.12.2-0ubuntu3 - how can I go about this? Thanks,

---

### Post by Ramses de Norre on 2007-01-31
Can you post the output of following commands:
```
apt-cache policy libpango1.0-0
apt-cache policy libgtk2.0-0
```
Those will show you which versions are in which repo, then if for example they are in main you do ```
sudo aptitude install package/dapper
```
If they are in dapper-updates you change "dapper" by "dapper-updates".

---

### Post by jaybee99 on 2007-01-31
Thankyou! That has fixed it.

I got :

```
titus@dandelion:~/gtk2hs-0.9.10$ apt-cache policy libpango1.0-0
libpango1.0-0:
  Installed: 1.12.3-0ubuntu3
  Candidate: 1.12.3-0ubuntu3
  Version table:
 *** 1.12.3-0ubuntu3 0
        100 /var/lib/dpkg/status
     1.12.2-0ubuntu3 0
        500 http://gb.archive.ubuntu.com dapper/main Packages

```
and ran
```

$ sudo aptitude install libpango1.0-0/dapper

```

---

