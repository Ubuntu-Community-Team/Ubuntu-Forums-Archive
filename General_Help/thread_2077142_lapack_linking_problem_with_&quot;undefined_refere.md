---
title: "lapack linking problem with &quot;undefined reference to&quot;"
date: 2012-10-27
forum: General Help
---

### Post by subjugater on 2012-10-27
I am trying to compile a simple fortran script, which I have successfully compiled on my old Ubuntu system 10.04.
```

PROGRAM TEST      
IMPLICIT NONE
REAL*8 :: X(2,3)
REAL*8 :: Y(3)=(/2.D0, 2.D0, 2.D0/)
REAL*8 :: Z(2)
X(1,:) = (/1.D0, 2.D0, 3.D0/)
X(2,:) = (/4.D0, 5.D0, 6.D0/)
CALL DGEMV('N', 2, 3, 1.D0, X, 2, Y, 1, 0.D0, Z, 1)
PRINT *, Z
END PROGRAM TEST

```
But now on Ubuntu 12.04, the following command line doesn't work.
```

gfortran -lblas -llapack test.f90

``` 

I learned a rumor that Ubuntu 12.04 doesn't search libraries for you. So I searched the location of lapack and blas on my machine.
BLAS:
```

kent@kent-laptop:~/Desktop/absorb$ dpkg --listfiles libblas-dev
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libblas-dev
/usr/share/doc/libblas-dev/copyright
/usr/lib
/usr/lib/libblas
/usr/lib/libblas/libblas.a
/usr/include
/usr/include/cblas_f77.h
/usr/include/cblas.h
/usr/share/doc/libblas-dev/README.Debian.gz
/usr/share/doc/libblas-dev/test_results.gz
/usr/share/doc/libblas-dev/changelog.Debian.gz
/usr/lib/libblas/libblas.so

```
LAPACK:
```

kent@kent-laptop:~/Desktop/absorb$ dpkg --listfiles liblapack-dev
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/liblapack-dev
/usr/share/doc/liblapack-dev/copyright
/usr/lib
/usr/lib/lapack
/usr/lib/lapack/liblapack.a
/usr/share/doc/liblapack-dev/changelog.Debian.gz
/usr/lib/lapack/liblapack.so

```
So I also tried by providing possible locations of these libraries. But the problem persists.
```

kent@kent-laptop:~/Desktop/lapack$ gfortran -lblas -llapack -L/usr/lib/libblas -L/usr/lib/lapack -L/usr/share/doc -L/usr/share test.f90
/tmp/cc6TbhaV.o: In function `MAIN__':
test.f90:(.text+0xa6): undefined reference to `dgemv_'
collect2: ld returned 1 exit status

```

Can anyone give me some clue? Thanks a lot!

---

