---
title: "gcc compile errors"
date: 2007-06-06
forum: General Help
---

### Post by Compactman on 2007-06-06
make[3]: *** [java/parse-scan.o] Error 1
make[3]: Leaving directory `/home/brad/Desktop/gcc-4.2.0/host-i686-pc-linux-gnu/gcc'
make[2]: *** [all-stage2-gcc] Error 2
make[2]: Leaving directory `/home/brad/Desktop/gcc-4.2.0'
make[1]: *** [stage2-bubble] Error 2
make[1]: Leaving directory `/home/brad/Desktop/gcc-4.2.0'
make: *** [all] Error 2
brad@brad-laptop:~/Desktop/gcc-4.2.0$ sudo make install
Password:
make[1]: Entering directory `/home/brad/Desktop/gcc-4.2.0'
/bin/sh ./mkinstalldirs /usr/local /usr/local
cd: 5: can't cd to host-i686-pc-linux-gnu/fixincludes
make[1]: *** [install-fixincludes] Error 2
make[1]: Leaving directory `/home/brad/Desktop/gcc-4.2.0'
make: *** [install] Error 2

---

### Post by taurus on 2007-06-06
Are you trying to build GCC-4.2.0?

---

### Post by Compactman on 2007-06-07
Yes sir!

---

