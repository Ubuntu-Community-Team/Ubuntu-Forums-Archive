---
title: "libc not found?"
date: 2008-02-25
forum: General Help
---

### Post by treehouse on 2008-02-25
I've been having issues with Ubuntu not detecting libc6. Gdebi package installer has given me the "dependency not satisfied: libc6" error for a few different things and now I got this:

```

$ openlierox
openlierox: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by openlierox)

```

When I look in Synaptic, libc6, libc6-dev, and libc6-i686 are all installed.

Any help would be appreciated.

Thanks.

---

### Post by Zeroangel on 2008-02-25
Have you installed the package using aptitude/synaptic or compiled it? If you have compiled the package you may need to set certain flags during the make process.

You could also try searching for any additional packages related to libc6
[URL="http://apt-cache%20search%20--names-only%20libc6"]```
apt-cache search --names-only libc6[/URL]
```
Sometimes theres weird alternate versions of packages in the repositories, like maybe a libc6-1.6 and libc6-2.0 (this is just an example, not actual packages).

You could also try reconfiguring the packages
[URL="http://sudo%20dpkg-reconfigure%20libc6"]```
sudo dpkg-reconfigure libc6
```[/URL]

Aaand, i'm not sure if its safe to do so, but if its a persistent problem theres always:
```
sudo apt-get remove --purge libc6*
```
```
sudo apt-get install libc6 libc6-dev WhatEverElseWasPurged
```

---

### Post by albertz on 2008-02-25
Which version of OpenLieroX have you tried? The recent Beta4?

It seems you have an old version of Ubuntu. Have you installed all recent updates?

Have you tried the suggestions by Zeroangel? Whereby I would be very carefull before you remove libc6, a lot of applications will not work without (perhaps also not apt-get and then you are in serious trouble...).

---

