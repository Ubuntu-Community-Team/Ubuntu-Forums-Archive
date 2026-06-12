---
title: "PyOpeNNi"
date: 2013-11-27
forum: General Help
---

### Post by sandsound2 on 2013-11-27
Hi I am using ubuntu 12.04 ant Python version 2.7

I tried PyOpeNNi instalation guide [https://github.com/jmendeth/PyOpenNI/wiki/Building-on-Linux](https://github.com/jmendeth/PyOpenNI/wiki/Building-on-Linux) but unfortunatelly i got this error while doing "make"

Linking CXX shared library ../lib/openni.so
/usr/bin/ld: /usr/local/lib/libpython2.7.a(abstract.o): relocation R_X86_64_32S against `_Py_NotImplementedStruct' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libpython2.7.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [lib/openni.so] Error 1
make[1]: *** [src/CMakeFiles/PyOpenNI.dir/all] Error 2
make: *** [all] Error 2

---

