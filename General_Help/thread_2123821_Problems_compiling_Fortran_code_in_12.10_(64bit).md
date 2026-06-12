---
title: "Problems compiling Fortran code in 12.10 (64bit)"
date: 2013-03-09
forum: General Help
---

### Post by mangaloreman on 2013-03-09
I am having trouble compiling a piece of Fortran code in Ubuntu 12.10 (64bit). I've installed gfortran and fftw3 (my code needs the fftw library) from Ubuntu software center. 

This is what I get when I try to compile the code:

```
/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
/usr/bin/ld: cannot find -lfftw3
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgfortran.so when searching for -lgfortran
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgfortran.a when searching for -lgfortran
/usr/bin/ld: cannot find -lgfortran
/usr/bin/ld: cannot find -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libquadmath.so when searching for -lquadmath
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libquadmath.a when searching for -lquadmath
/usr/bin/ld: cannot find -lquadmath
/usr/bin/ld: cannot find -lm
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: cannot find -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: cannot find crtn.o: No such file or directory
collect2: error: ld returned 1 exit status
make: *** [ib] Error 1

```
Please help!

---

### Post by gordintoronto on 2013-03-09
Have you installed build-essential?

---

### Post by mangaloreman on 2013-03-09
I just installed build-essential and then re-installed gfortran and fftw3, but I still get the same error messages as above.

---

