---
title: "compiling High Performance Computing Linpack Benchmark"
date: 2008-04-30
forum: General Help
---

### Post by HPCE_Larry on 2008-04-30
I'm trying to compile HPL to get the flops performance of my computer. In short, I'm building a beowulf cluster and this program is evidently what is used to benchmark one. I figured that I would try it on my home computer first for comparisons sake. However, I'm having some trouble compiling it.

The instructions read
```
 1) Retrieve the tar file, then

    gunzip hpl.tgz; tar -xvf hpl.tar

 this  will create an  hpl  directory,  that we call below the
 top-level directory.

 2) Create a file Make.<arch> in the  top-level directory. For
 this purpose,  you  may  want  to re-use one contained in the
 setup directory. This file essentially contains the compilers
 and librairies with their paths to be used.

 3) Type "make arch=<arch>". This  should create an executable
 in the bin/<arch> directory called xhpl.

 For example, on our Linux PII cluster, I create a file called
 Make.Linux_PII in the top-level directory. Then, I type
    "make arch=Linux_PII" 
 This creates the executable file bin/Linux_PII/xhpl.
```

Seems simple enough. I create a file Make.HPL in the directory and type
```
sudo make arch=HPL
```
at which point i get a bunch of scrolling text that generally repeats itself and doesn't stop till I hit ctrl+c. 
Sample:
```
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.blas     src/blas/HPL/Makefile
make[27]: execvp: makes/Make.blas: Permission denied
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.comm     src/comm/HPL/Makefile
make[27]: execvp: makes/Make.comm: Permission denied
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.grid     src/grid/HPL/Makefile
make[27]: execvp: makes/Make.grid: Permission denied
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.panel    src/panel/HPL/Makefile
make[27]: execvp: makes/Make.panel: Permission denied
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.pauxil   src/pauxil/HPL/Makefile
make[27]: execvp: makes/Make.pauxil: Permission denied
make[27]: [refresh_src] Error 127 (ignored)
makes/Make.pfact    src/pfact/HPL/Makefile
make[27]: execvp: makes/Make.pfact: Permission denied

```

What am I doing wrong?

---

### Post by GrandTheft on 2010-07-20
Hi,

I have got the same problem here. Any new ideas?

GT

---

### Post by emil.s on 2010-10-13
Hello! I'm also trying to get HPL working...

I get:
```
make[2]: [leaf] Error 1 (ignored)
( cd src/pfact/Linux_P2 ; \
            ln -s /home/emil/hpl/Make.Linux_P2 Make.inc )
In file included from /home/emil/hpl/include/hpl.h:80,
                 from ../HPL_fprintf.c:50:
/home/emil/hpl/include/hpl_pmisc.h:54:17: error: mpi.h: No such file or directory
```

In "hpl_pmisc.h" there is just the normal "include mpi.h".

I got an mpi.h in /usr/include/mpich2/mpi.h, but how do I get make search there?

---

### Post by GrandTheft on 2010-10-13
If you're interested in benchmarking intel cpus only, 

[http://software.intel.com/en-us/articles/intel-math-akernel-library-linpack-download/](http://software.intel.com/en-us/articles/intel-math-akernel-library-linpack-download/)

will help.

Still, I would be very interested if someone managed to compile it and wants give some instructions.

Best regards,
GT

---

### Post by Manyrootsofallevil on 2012-04-19
> **GrandTheft said:**
> If you're interested in benchmarking intel cpus only, 

[http://software.intel.com/en-us/articles/intel-math-akernel-library-linpack-download/](http://software.intel.com/en-us/articles/intel-math-akernel-library-linpack-download/)

will help.

Still, I would be very interested if someone managed to compile it and wants give some instructions.

Best regards,
GT

Link seems to be dead, found this though.

[http://software.intel.com/en-us/articles/intel-math-kernel-library-linpack-download/](http://software.intel.com/en-us/articles/intel-math-kernel-library-linpack-download/)

---

### Post by Manyrootsofallevil on 2012-04-19
Found a solution

on the make file comment the MPI section and change the compiler/linker section like below. The mpicc wrapper will deal with the dependencies.

```
# ----------------------------------------------------------------------
# - Message Passing library (MPI) --------------------------------------
# ----------------------------------------------------------------------
# MPinc tells the  C  compiler where to find the Message Passing library
# header files,  MPlib  is defined  to be the name of  the library to be
# used. The variable MPdir is only used for defining MPinc and MPlib.
#
#MPdir        = /usr/lib64/mpich2
#MPinc        = -I$(MPdir)/include
#MPlib        = $(MPdir)/lib/libmpich.a

# ----------------------------------------------------------------------
# - Compilers / linkers - Optimization flags ---------------------------
# ----------------------------------------------------------------------
#
CC           = /usr/bin/mpicc
CCNOOPT      = $(HPL_DEFS)
CCFLAGS      = $(HPL_DEFS) -fomit-frame-pointer -O3 -funroll-loops
#
# On some platforms,  it is necessary  to use the Fortran linker to find
# the Fortran internals used in the BLAS library.
#
LINKER       = /usr/bin/mpicc
LINKFLAGS    = $(CCFLAGS)
#


```

---

### Post by overdrank on 2012-04-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

