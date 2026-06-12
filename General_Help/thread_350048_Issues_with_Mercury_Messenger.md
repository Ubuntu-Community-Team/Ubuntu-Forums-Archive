---
title: "Issues with Mercury Messenger"
date: 2007-01-31
forum: General Help
---

### Post by Maelgwyn on 2007-01-31
Hey guys,

I've just installed Mercury Messenger from [this site]("http://projeto-messias.sourceforge.net/"), and Java from Automatix2. When I try to run mercury from the command-line (I'm using fluxbox on top of a standard 6.10 Ubuntu install) I get the following error message:

```
haakuturi@tane:~$ mercury
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
haakuturi@tane:~$ 
```

Any ideas? :(

---

### Post by renzokuken on 2007-01-31
looks like you have some unmet dependencies. not quite sure which package librt,libm and libc are in. i found something mentioning libcsc on google.

have a look for it in synaptic

---

### Post by pipolibo on 2007-03-21
Did you start mercury as root the first time?

---

