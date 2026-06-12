---
title: "Make Install Issue"
date: 2007-12-11
forum: General Help
---

### Post by kamikazejustin on 2007-12-11
I have tried in the past to "make install" a variety of packages and they always fail. I'm trying to configure a package for a snort install and this is the error I'm getting.



root@penguinbox:~/snorttmp/pcre-7.4# make check
source='pcrecpp.cc' object='pcrecpp.lo' libtool=yes \
        DEPDIR=.deps depmode=none /bin/bash ./depcomp \
        /bin/bash ./libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I.      -c -o pcrecpp.lo pcrecpp.cc
libtool: ignoring unknown tag CXX
 g++ -DHAVE_CONFIG_H -I. -c pcrecpp.cc  -fPIC -DPIC -o .libs/pcrecpp.o
./libtool: line 1325: g++: command not found
make: *** [pcrecpp.lo] Error 1



Please help????

---

### Post by taurus on 2007-12-11
Have you installed the build-essential package before you try to compile anything from a terminal?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

