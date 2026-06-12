---
title: "Need help with ./autogen.sh"
date: 2006-08-28
forum: General Help
---

### Post by Scorpuk on 2006-08-28
I am trying to install lirc, but it needs to use ./autogen.sh


Apparently I need libtool-1.3.3, automake-1.4 and autoconf-2.13, but don't know what to type at the cli. :(


Using cli becuase I am away from the computer and using putty to log in.


Tnx for any help.

---

### Post by duff on 2006-08-29
Serch for packages using

```
# apt-cache search --names-only libtool
```

Leave off the "--name-only" to search descriptions.

When you find what you want to install

```
# sudo apt-get install libtool
```

---

