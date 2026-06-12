---
title: "cannot open libjvm.so"
date: 2008-01-09
forum: General Help
---

### Post by Joshua Swink on 2008-01-09
Ok, the title of this post is a lie, because I did eventually get libjvm.so to load. But I wanted to know if anyone has a better way.

I want to use R and its Java graphical interface, JGR. Simply installing sun-java6-bin did not make this possible, because JGR still couldn't find libjvm.so.

My solution was to create /etc/ld.so.conf.d/java-jre.conf containing:

```
/usr/lib/jvm/java-6-sun/jre/lib/i386
/usr/lib/jvm/java-6-sun/jre/lib/i386/client

```

And then to run:

```
$ ldconfig
```

It seems odd that the sun-java6-jre package doesn't set the system up to use its libraries. Manually updating the dynamic loader cache is kludgy. Does anyone have a better solution?

---

