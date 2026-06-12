---
title: "not able to find plf repo"
date: 2006-07-16
forum: General Help
---

### Post by kinematic on 2006-07-16
anyone else getting this error message when trying to add the plf repo?
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found

---

### Post by Ramses de Norre on 2006-07-16
For some reason the url changed a bit, this one should work:
```
## Dapper PLF repository
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```

---

### Post by glennric on 2006-07-16
The PLF repositories apparently have been restructured.  I have been getting these errors for the last week.  Finally I looked at the structure of the website and figured it out.  The lines in your sources.list file should be

```

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```

---

### Post by kinematic on 2006-07-16
thnx..that worked :D

---

