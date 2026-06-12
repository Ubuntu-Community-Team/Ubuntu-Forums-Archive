---
title: "Another Sysinfo ?"
date: 2007-02-20
forum: General Help
---

### Post by tipping point on 2007-02-20
Does Sysinfo work at all in Edgy? I know the one in the repos doesn't but what about the download available on Sourceforge? I'm new but these install instructions need some clarification.
   1. tar xvfz sysinfo-XXX.tar.gz (extract the source tarball)
   2. cd syinfo-XXX (cd into source root directory)
   3. ./configure –prefix=/usr (run configure script with /usr prefix)
   4. make (compile)
   5. su -c make install (install + enter root password)
Ive tried them and keep getting errors during install, if anyone can make helpful changes to these instructions it would be appreciated.
I understand #1 and 2 but not exactly what I am supposed to type for #3, now if I get that right #4 and 5 should complete install.

---

### Post by ewankho on 2007-02-20
I think you need to type 
```
./configure –prefix=/usr
```
in the terminal.

---

