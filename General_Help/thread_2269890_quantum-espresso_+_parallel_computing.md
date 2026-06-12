---
title: "quantum-espresso + parallel computing"
date: 2015-03-18
forum: General Help
---

### Post by markodd on 2015-03-18
Hey there,

quantum-espresso is a software that's available in the ubuntu repositories, meaning one can install it by using the usual "apt-get install quantum-espresso". However, that is an old version and I want/need a newer one, which is available at: [http://www.qe-forge.org/gf/project/q-e/frs/?action=FrsReleaseBrowse&frs_package_id=18](http://www.qe-forge.org/gf/project/q-e/frs/?action=FrsReleaseBrowse&frs_package_id=18)

I've followed [this]("http://conquer-ur-computer.blogspot.com/2010/12/install-quantum-espresso-in-ubuntu.html") tutorial for installing and it works well in serial. I need it to work in parallel though. The version available in the repositories works flawlessly, both in serial and in parallel. This gives me the impression that it's probably a small mistake I am making, probably in the path or something.

When doing "./configure" I get the following:

Parallel environment not detected \(is this a parallel machine?\).\
Configured for compilation of serial executables.


So ya, please let me know if you can help me in any way, I'd be very thankful.

---

### Post by plurga on 2015-03-18
have check if this is supported on the ubuntu version that u are using ? 

in the other hand pls check on [COLOR=#000000]quantum-espresso official webpage ! [/COLOR]

---

### Post by markodd on 2015-03-19
> **plurga said:**
> have check if this is supported on the ubuntu version that u are using ? 

in the other hand pls check on [COLOR=#000000]quantum-espresso official webpage ! [/COLOR]

I did check and they're not very helpful, sadly.

---

### Post by monkeybrain20122 on 2015-03-19
I don't know anything about this software but just a guess, maybe you need openmpi or something like that  installed. Check your configure log.

---

### Post by markodd on 2015-03-19
> **monkeybrain20122 said:**
> I don't know anything about this software but just a guess, maybe you need openmpi or something like that  installed. Check your configure log.

I have openmpi installed. In fact I run the software by doing "mpirun -np 4 pw.x". I think the problem might have something to do with paths. Parallel computing works fine if I installed the version available in the repositories. If I compile the latest version, however, I cannot make it work.

Below is the output of ./configure:

```
[EMAIL="markod@markodspc:~/.espres"]markod@markodspc:~/.espres[/EMAIL]so-5.1.2$ ./configure 
checking build system type... x86_64-unknown-linux-gnu
detected architecture... x86_64
checking for ifort... no
checking for pgf90... no
checking for pathf95... no
checking for sunf95... no
checking for openf95... no
checking for gfortran... gfortran
configure: WARNING: using cross tools not prefixed with host triplet
checking for Fortran compiler default output file name... a.out
checking whether the Fortran compiler works... yes
checking whether we are cross compiling... yes
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU Fortran compiler... yes
checking whether gfortran accepts -g... yes
checking for Fortran flag to compile .f90 files... none
checking for mpif90... no
checking for gfortran... gfortran
checking whether we are using the GNU Fortran compiler... yes
checking whether gfortran accepts -g... yes
checking version of gfortran... gfortran 4.8.2
setting F90... gfortran
setting MPIF90... gfortran
checking for cc... cc
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
setting CC... cc
checking how to run the C preprocessor... cc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking size of int *... 8
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for struct mallinfo.arena... yes
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
setting F77... gfortran
using F90... gfortran
setting FFLAGS... -O3 -g
setting F90FLAGS... $(FFLAGS) -x f95-cpp-input
setting FFLAGS_NOOPT... -O0 -g
setting CFLAGS... -O3
setting CPP... cpp
setting CPPFLAGS... -P -C -traditional
setting LD... gfortran
setting LDFLAGS... -g -pthread
setting AR... ar
setting ARFLAGS... ruv
checking whether make sets $(MAKE)... yes
checking whether Fortran files must be preprocessed... no
checking how to get verbose linking output from gfortran... -v
checking for Fortran 77 libraries of gfortran...  -L/usr/lib/gcc/x86_64-linux-gnu/4.8 -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib -L/lib/x86_64-linux-gnu -L/lib/../lib -L/usr/lib/x86_64-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.8/../../.. -lgfortran -lm -lquadmath
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... lower case, underscore, no extra underscore
checking for library containing dgemm... no
MKL not found
in /opt/intel/composer*/mkl/lib/intel64: checking for library containing dgemm... no
MKL not found
in /opt/intel/Compiler/*/*/mkl/lib/em64t: checking for library containing dgemm... no
MKL not found
in /opt/intel/mkl/*/lib/em64t: checking for library containing dgemm... no
MKL not found
in /opt/intel/mkl*/lib/em64t: checking for library containing dgemm... no
MKL not found
in /opt/intel/mkl/lib: checking for library containing dgemm... no
MKL not found
checking for library containing dgemm... no
in /usr/local/lib: checking for library containing dgemm... no
checking for library containing dgemm... -lblas
checking for library containing dspev... -llapack
setting BLAS_LIBS... -lblas
setting LAPACK_LIBS... -llapack -lblas
checking for library containing dfftw_execute_dft... -lfftw3
setting FFT_LIBS... -lfftw3
setting MASS_LIBS...
checking for library containing mpi_init... no
setting MPI_LIBS...
checking for library containing mpi_init... (cached) no
setting SCALAPACK_LIBS...
setting DFLAGS... -D__GFORTRAN -D__STD_F95 -D__FFTW3
setting IFLAGS... -I../include
setting FDFLAGS... $(DFLAGS)
checking for ranlib... ranlib
setting RANLIB... ranlib
checking for wget... wget -O
setting WGET... wget -O
configure: creating ./config.status
config.status: creating include/fft_defs.h
config.status: creating make.sys
config.status: creating configure.msg
config.status: creating install/make_wannier90.sys
config.status: creating install/make_blas.inc
config.status: creating install/make_lapack.inc
config.status: creating include/c_defs.h
config.status: include/c_defs.h is unchanged
--------------------------------------------------------------------
ESPRESSO can take advantage of several optimized numerical libraries
(essl, fftw, mkl...).  This configure script attempts to find them,
but may fail if they have been installed in non-standard locations.
If a required library is not found, the local copy will be compiled.

The following libraries have been found:
  BLAS_LIBS= -lblas 
  LAPACK_LIBS= -llapack  -lblas 
  FFT_LIBS= -lfftw3 
Please check if this is what you expect.

If any libraries are missing, you may specify a list of directories
to search and retry, as follows:
  ./configure LIBDIRS="list of directories, separated by spaces"

Parallel environment not detected \(is this a parallel machine?\).\
Configured for compilation of serial executables.

For more info, read the ESPRESSO User's Guide (Doc/users-guide.tex).
--------------------------------------------------------------------
configure: success
mv: try to overwrite ‘./install/config.log’, overriding mode 0644 (rw-r--r--)?
```

---

### Post by dragonfly41 on 2015-03-19
I have no prior knowledge of quantum-espresso but it is an interesting suite.

Re: not recognising parallel environment ... see FAQ 15

[http://www.quantum-espresso.org/faq/installationwww/#1.5](http://www.quantum-espresso.org/faq/installationwww/#1.5)

The quantum-espresso forum should give you more information ...

[http://www.quantum-espresso.org/forum/](http://www.quantum-espresso.org/forum/)

e.g. on the failure to compute parallel ...

[http://www.mail-archive.com/pw_forum%40pwscf.org/msg17678.html](http://www.mail-archive.com/pw_forum%40pwscf.org/msg17678.html)

[http://www.mail-archive.com/pw_forum%40pwscf.org/msg14544.html](http://www.mail-archive.com/pw_forum%40pwscf.org/msg14544.html)

Exploring further .. for more information on dependencies in Ubuntu run the command

apt-cache depends quantum-espresso

Do you have these dependencies (as listed) installed?  
Use Synaptic Package Manager to search for these.

And the reverse dependencies are found with this command .

apt-cache rdepends quantum-espresso

```

output ...
quantum-espresso
Reverse Depends:
  science-physics
  science-nanoscale-physics
  quantum-espresso-data
  debichem-abinitio

```

Perhaps you can get some clues from above.

---

### Post by markodd on 2015-03-19
I've fixed the problem by installing ```
libopenmpi-dev
```

Thanks to those who replied to the thread.

---

### Post by dragonfly41 on 2015-03-19
That's good .. running command ... apt-cache depends quantum-espresso ... on the earlier version 
did show this dependency .. amongst many .. but *not* libopenmpi-dev

 Depends: libopenmpi1.6

Suggest that you now mark this thread as SOLVED.

---

### Post by monkeybrain20122 on 2015-03-20
> **markodd said:**
> I've fixed the problem by installing ```
libopenmpi-dev
```

Thanks to those who replied to the thread.

I should have been clearer on this. When you compile something from source you always need the dev file, so when it says you need libopenmpi you have to actually install its -dev file (which would pull in libopenmpi)

---

