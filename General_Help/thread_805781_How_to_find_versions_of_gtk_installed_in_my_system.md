---
title: "How to find versions of gtk installed in my system"
date: 2008-05-24
forum: General Help
---

### Post by dayanandasaraswati on 2008-05-24
Hi, i want to find the versions of gtk, glib, cairo and pango installed in my system. I've a hardy heron machine and I've seen the /usr/lib directory, I've all the gtk, glib,pango and cairo library files. But i want a command to find the versions of them. Help me out.

---

### Post by jrib on 2008-05-24
> **dayanandasaraswati said:**
> Hi, i want to find the versions of gtk, glib, cairo and pango installed in my system. I've a hardy heron machine and I've seen the /usr/lib directory, I've all the gtk, glib,pango and cairo library files. But i want a command to find the versions of them. Help me out.

```
apt-cache policy PACKAGE
```
will give you PACKAGE's version

Also, depending on why exactly you want this, 
```
pkg-config --modversion LIBRARY
```
may be useful.

Why do you want this by the way?

---

