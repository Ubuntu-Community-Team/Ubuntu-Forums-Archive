---
title: "Can't compile beryl from svn"
date: 2006-11-15
forum: General Help
---

### Post by juraj on 2006-11-15
I've checked out beryl from their svn repository and have tried to compile it, but with no success. When I run ./automake or make I get this:

aclocal: macro `AM_PATH_PYTHON' required but not defined

And whole compilation fails. What's that? How do I get it?

PS: I've tried the svn rep for dapper and when I try installing beryl from there it complains about outdated libc6 and others. Sounds like the rep is made for edgy.

Please... help. TIA

---

### Post by ser1alsn1per on 2006-11-15
[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

chose the right one and hope fully it helps

---

### Post by Horizon on 2006-12-24
In case anyone is wondering, running 
```
sudo apt-get install automake1.9
```
did the trick. Apparently apt-get'ing "automake" gets 1.4!?

---

