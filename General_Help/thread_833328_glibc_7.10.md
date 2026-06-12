---
title: "glibc 7.10"
date: 2008-06-18
forum: General Help
---

### Post by alphaniner on 2008-06-18
This is probably a stupid question, but how do I find what version of glibc I have installed (assuming I have it installed)?  In synaptic I could only find glibc-doc.  I did a command line search using locate and only found /etc/init.d/glibc.sh.  Thanks.

---

### Post by geraldm on 2008-06-18
The glibc version is contained within the name of the libraries of the package, 
ld-2.5.1.so libanl.2.5.1.so libm-2.5.1.so 
It is also in the executables, returned by passing "--version" to the executable

Libs:
libBrokenLocale-2.5.1.so 
  etc..

Executables:
gencat genent mtrace xtrace

mtrace --version

Gerald

---

