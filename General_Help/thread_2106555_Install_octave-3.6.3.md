---
title: "Install octave-3.6.3?"
date: 2013-01-19
forum: General Help
---

### Post by fr33c0untry on 2013-01-19
hi i've been trying to install octave-3.6.3  for several days but with no success.i followed the steps that you've mentioned but i get this error when compiling
```

checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking if sgemm_ is being linked in already... no
checking for ATL_xerbla in -latlas... no
checking for sgemm_ in -lblas... yes
checking for dgemm_ in -ldgemm... no
checking for sgemm_ in -lmkl... no
checking for sgemm_ in -framework vecLib... no
checking for sgemm_ in -lcxml... no
checking for sgemm_ in -ldxml... no
checking for sgemm_ in -lscs... no
checking for sgemm_ in -lcomplib.sgimath... no
checking for sgemm_ in -lblas... (cached) yes
checking for sgemm_ in -lessl... no
checking for sgemm_ in -lblas... (cached) yes
checking whether LSAME is called correctly from Fortran... yes
checking whether ISAMAX is called correctly from Fortran... yes
checking whether SDOT is called correctly from Fortran... yes
checking whether DDOT is called correctly from Fortran... yes
checking whether CDOTU is called correctly from Fortran... yes
checking whether ZDOTU is called correctly from Fortran... yes
checking whether the integer size is correct... yes
checking for cheev_... no
checking for cheev_ in -llapack... no
checking for cheev_ in -llapack_rs6k... no
configure: error: You are required to have BLAS and LAPACK libraries

```
I get this error inspite of having installed libblas-dev (version 3.3.1)and liblapack-dev from the synaptic manager.
i downloaded LAPACK-3.4.2.tgz but dont know how to install it.do you think its necessary since it's the latest version?

later i installed octave-3.6.3 from the software center after giving up on compiling from the source.it downloaded fine but when i tried to make some 3d plots or use the eig() function i get the following error:
```

octave: symbol lookup error: /usr/lib/liblapack.so.3gf: undefined symbol: ATL_idamax

```
then it closes by itself.
i think there's an issue with the LAPACK OR BLAS libraries since its not able to perform many of the vital matrix manipulations.
looking forward for your help

---

### Post by oldos2er on 2013-01-19
Post moved to its own thread.

---

