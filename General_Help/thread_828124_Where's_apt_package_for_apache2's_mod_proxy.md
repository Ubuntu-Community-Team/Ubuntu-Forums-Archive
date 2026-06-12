---
title: "Where's apt package for apache2's mod_proxy?"
date: 2008-06-13
forum: General Help
---

### Post by tedder on 2008-06-13
I can't find the package for mod_proxy. Here's what I get from a search:
```
$ apt-cache search proxy | egrep -i "apach"
libapache2-mod-proxy-html - Apache2 filter module for HTML links rewriting
libapache2-mod-rpaf - module for Apache2 which takes the last IP from the 'X-Forwarded-For' header

```

Here's my version info:
```
$ cat /etc/debian_version
lenny/sid
$ uname -a
Linux motion-stgeorge 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

What's the name of the package? Is it in some nonstandard repository? (and why?)

---

