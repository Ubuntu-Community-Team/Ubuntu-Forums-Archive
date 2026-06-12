---
title: "TinaPOS - not compiling"
date: 2007-07-18
forum: General Help
---

### Post by daller on 2007-07-18
Hi there,

I'm trying to compile TinaPOS from [http://tinapos.sourceforge.net/](http://tinapos.sourceforge.net/)

I know it has a BIN package, but it's flawed (according to my own experience, and some on the forums...)

I have build-essential installed, and get this:

elav1@elav1-desktop:~/Desktop/tinapos_0_0_22_src/srcbuild$ sh configure.sh
Exception in thread "main" java.lang.NoClassDefFoundError: net/adrianromero/tpv/config/JFrmConfig

Do I need some Java build packages, and I such case, where do I get them?

---

### Post by taurus on 2007-07-18
Search for Sun's java in synaptic.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by daller on 2007-07-18
I have both Java6 runtime and JDK installed!

Any other ideas?

---

### Post by yabbadabbadont on 2007-07-18
In their english help forum, there is a thread on Linux issues that lists your exact error.  It was apparently caused by having more than one java environment installed on the machine at the same time.  The user solved the error by removing the extra java environments and only keeping the one from sun.

---

