---
title: "Trouble installing GCC 4.2.0"
date: 2007-01-16
forum: General Help
---

### Post by Stomstedt on 2007-01-16
I did the ./configure command and now I also just attempted a few other things such this:

owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ sudo make install
Password:
make[1]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
/bin/sh ./mkinstalldirs /usr/local /usr/local
/bin/sh: line 3: cd: host-i686-pc-linux-gnu/fixincludes: No such file or directory
make[1]: *** [install-fixincludes] Error 1
make[1]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make: *** [install] Error 2
owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ graal
graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by graal)
owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln works... (cached) yes
checking whether ln -s works... (cached) yes
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gnatbind... no
checking whether compiler driver understands Ada... (cached) no
checking how to compare bootstrapped objects... (cached) cmp --ignore-initial=16 $$f1 $$f2
checking for correct version of gmp.h... no
The following languages will be built: c,c++,java,objc
*** This configuration is not supported in the following subdirectories:
     target-libada gnattools target-libgfortran
    (Any other directories should still work fine.)
*** removing build-i686-pc-linux-gnu/libiberty/Makefile to force reconfigure
*** removing build-i686-pc-linux-gnu/fixincludes/Makefile to force reconfigure
checking for bison... no
checking for byacc... no
checking for yacc... no
checking for bison... no
checking for gm4... no
checking for gnum4... no
checking for m4... no
checking for flex... no
checking for lex... no
checking for flex... no
checking for makeinfo... no
checking for expect... no
checking for runtest... no
checking for i686-pc-linux-gnu-ar... (cached) ar
checking for i686-pc-linux-gnu-as... (cached) as
checking for i686-pc-linux-gnu-dlltool... no
checking for dlltool... no
checking for i686-pc-linux-gnu-ld... (cached) ld
checking for i686-pc-linux-gnu-lipo... no
checking for lipo... no
checking for i686-pc-linux-gnu-nm... (cached) nm
checking for i686-pc-linux-gnu-ranlib... (cached) ranlib
checking for i686-pc-linux-gnu-strip... (cached) strip
checking for i686-pc-linux-gnu-windres... no
checking for windres... no
checking for i686-pc-linux-gnu-objcopy... (cached) objcopy
checking for i686-pc-linux-gnu-objdump... (cached) objdump
checking for i686-pc-linux-gnu-gcj... no
checking for gcj... no
checking for i686-pc-linux-gnu-gfortran... no
checking for gfortran... no
checking for ar... no
checking for as... no
checking for dlltool... no
checking for i686-pc-linux-gnu-dlltool... no
checking for dlltool... no
checking for ld... no
checking for lipo... no
checking for i686-pc-linux-gnu-lipo... no
checking for lipo... no
checking for nm... no
checking for objdump... no
checking for ranlib... no
checking for strip... no
checking for windres... no
checking for i686-pc-linux-gnu-windres... no
checking for windres... no
checking where to find the target ar... host tool
checking where to find the target as... host tool
checking where to find the target cc... just compiled
checking where to find the target c++... just compiled
checking where to find the target c++ for libstdc++... just compiled
checking where to find the target dlltool... host tool
checking where to find the target gcc... just compiled
checking where to find the target gcj... just compiled
checking where to find the target gfortran... host tool
checking where to find the target ld... host tool
checking where to find the target lipo... host tool
checking where to find the target nm... host tool
checking where to find the target objdump... host tool
checking where to find the target ranlib... host tool
checking where to find the target strip... host tool
checking where to find the target windres... host tool
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether -fkeep-inline-functions is supported... yes
creating ./config.status
creating Makefile
owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ make
[ -f stage_final ] || echo stage3 > stage_final
make[1]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
make[2]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
rm -f stage_current
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make[2]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make[2]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libiberty'
make[4]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libiberty/testsuite'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libiberty/testsuite'
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libiberty'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/intl'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/intl'
Configuring in build-i686-pc-linux-gnu/libiberty
configure: loading cache ../config.cache
checking whether to enable maintainer-specific portions of Makefiles... no
checking for makeinfo... (cached) /home/owner/Desktop/gcc-4.2-20070110/missing makeinfo --split-size=5000000 --split-size=5000000
configure: WARNING:
*** Makeinfo is missing. Info documentation will not be built.
checking for perl... (cached) perl
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking for i686-pc-linux-gnu-ar... no
checking for ar... (cached) ar
checking for i686-pc-linux-gnu-ranlib... no
checking for ranlib... (cached) ranlib
checking for i686-pc-linux-gnu-gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking how to run the C preprocessor... (cached) gcc -E
checking whether gcc accepts -Wc++-compat... (cached) no
checking whether gcc and cc understand -c and -o together... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking for inline... (cached) inline
checking whether byte ordering is bigendian... (cached) no
checking for a BSD-compatible install... /usr/bin/install -c
checking for sys/file.h... (cached) yes
checking for sys/param.h... (cached) yes
checking for limits.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for malloc.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for strings.h... (cached) yes
checking for sys/time.h... (cached) yes
checking for time.h... (cached) yes
checking for sys/resource.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for sys/mman.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for alloca.h... (cached) yes
checking for sys/pstat.h... (cached) no
checking for sys/sysmp.h... (cached) no
checking for sys/sysinfo.h... (cached) yes
checking for machine/hal_sysinfo.h... (cached) no
checking for sys/table.h... (cached) no
checking for sys/sysctl.h... (cached) yes
checking for sys/systemcfg.h... (cached) no
checking for stdint.h... (cached) yes
checking for stdio_ext.h... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... (cached) yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking whether errno must be declared... (cached) no
checking for egrep... (cached) grep -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for int... (cached) yes
checking size of int... (cached) 4
checking for uintptr_t... (cached) yes
checking for a 64-bit type... (cached) uint64_t
checking for pid_t... (cached) yes
checking for library containing strerror... (cached) none required
checking for asprintf... (cached) yes
checking for atexit... (cached) yes
checking for basename... (cached) yes
checking for bcmp... (cached) yes
checking for bcopy... (cached) yes
checking for bsearch... (cached) yes
checking for bzero... (cached) yes
checking for calloc... (cached) yes
checking for clock... (cached) yes
checking for ffs... (cached) yes
checking for getcwd... (cached) yes
checking for getpagesize... (cached) yes
checking for gettimeofday... (cached) yes
checking for index... (cached) yes
checking for insque... (cached) yes
checking for memchr... (cached) yes
checking for memcmp... (cached) yes
checking for memcpy... (cached) yes
checking for memmove... (cached) yes
checking for mempcpy... (cached) yes
checking for memset... (cached) yes
checking for mkstemps... (cached) no
checking for putenv... (cached) yes
checking for random... (cached) yes
checking for rename... (cached) yes
checking for rindex... (cached) yes
checking for setenv... (cached) yes
checking for snprintf... (cached) yes
checking for sigsetmask... (cached) yes
checking for stpcpy... (cached) yes
checking for stpncpy... (cached) yes
checking for strcasecmp... (cached) yes
checking for strchr... (cached) yes
checking for strdup... (cached) yes
checking for strncasecmp... (cached) yes
checking for strndup... (cached) yes
checking for strrchr... (cached) yes
checking for strstr... (cached) yes
checking for strtod... (cached) yes
checking for strtol... (cached) yes
checking for strtoul... (cached) yes
checking for strverscmp... (cached) yes
checking for tmpnam... (cached) yes
checking for vasprintf... (cached) yes
checking for vfprintf... (cached) yes
checking for vprintf... (cached) yes
checking for vsnprintf... (cached) yes
checking for vsprintf... (cached) yes
checking for waitpid... (cached) yes
checking whether alloca needs Cray hooks... (cached) no
checking stack direction for C alloca... (cached) -1
checking for unistd.h... (cached) yes
checking for vfork.h... (cached) no
checking for fork... (cached) yes
checking for vfork... (cached) yes
checking for working fork... (cached) yes
checking for working vfork... (cached) yes
checking for _doprnt... (cached) no
checking for sys_errlist... (cached) yes
checking for sys_nerr... (cached) yes
checking for sys_siglist... (cached) yes
checking for external symbol _system_configuration... no
checking for getrusage... (cached) yes
checking for on_exit... (cached) yes
checking for psignal... (cached) yes
checking for strerror... (cached) yes
checking for strsignal... (cached) yes
checking for sysconf... (cached) yes
checking for times... (cached) yes
checking for sbrk... (cached) yes
checking for gettimeofday... (cached) yes
checking for realpath... (cached) yes
checking for canonicalize_file_name... (cached) yes
checking for pstat_getstatic... (cached) no
checking for pstat_getdynamic... (cached) no
checking for sysmp... (cached) no
checking for getsysinfo... (cached) no
checking for table... (cached) no
checking for sysctl... (cached) yes
checking for wait3... (cached) yes
checking for wait4... (cached) yes
checking for __fsetlocking... (cached) yes
checking whether basename is declared... (cached) no
checking whether ffs is declared... (cached) yes
checking whether asprintf is declared... (cached) no
checking whether vasprintf is declared... (cached) no
checking whether snprintf is declared... (cached) yes
checking whether vsnprintf is declared... (cached) yes
checking whether calloc is declared... (cached) yes
checking whether getenv is declared... (cached) yes
checking whether getopt is declared... (cached) yes
checking whether malloc is declared... (cached) yes
checking whether realloc is declared... (cached) yes
checking whether sbrk is declared... (cached) yes
checking whether strverscmp is declared... (cached) no
checking whether canonicalize_file_name must be declared... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... (cached) yes
checking for working mmap... (cached) yes
checking for working strncmp... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating testsuite/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default commands
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/libiberty'
rm -f needed-list; touch needed-list; \
        for f in atexit calloc memchr memcmp memcpy memmove memset rename strchr strerror strncmp strrchr strstr strtol strtoul tmpnam vfprintf vprintf vfork waitpid bcmp bcopy bzero; do \
          for g in ./mkstemps.o ; do \
            case "$g" in \
              *$f*) echo $g >> needed-list ;; \
            esac; \
          done; \
        done
echo ./regex.o ./cplus-dem.o ./cp-demangle.o ./md5.o ./alloca.o ./argv.o ./choose-temp.o ./concat.o ./cp-demint.o ./dyn-string.o ./fdmatch.o ./fibheap.o ./floatformat.o ./fnmatch.o ./fopen_unlocked.o ./getopt.o ./getopt1.o ./getpwd.o ./getruntime.o ./hashtab.o ./hex.o ./lbasename.o ./lrealpath.o ./make-relative-prefix.o ./make-temp-file.o ./objalloc.o ./obstack.o ./partition.o ./pexecute.o ./physmem.o ./pex-common.o ./pex-one.o ./pex-unix.o ./safe-ctype.o ./sort.o ./spaces.o ./splay-tree.o ./strerror.o ./strsignal.o ./ternary.o ./unlink-if-ordinary.o ./xatexit.o ./xexit.o ./xmalloc.o ./xmemdup.o ./xstrdup.o ./xstrerror.o ./xstrndup.o > required-list
make[4]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/libiberty/testsuite'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/libiberty/testsuite'
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/libiberty'
Configuring in build-i686-pc-linux-gnu/fixincludes
configure: loading cache ../config.cache
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking target system type... (cached) i686-pc-linux-gnu
checking for i686-pc-linux-gnu-gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking whether gcc supports -W... (cached) yes
checking whether gcc supports -Wall... (cached) yes
checking whether gcc supports -Wwrite-strings... (cached) yes
checking whether gcc supports -Wstrict-prototypes... (cached) yes
checking whether gcc supports -Wmissing-prototypes... (cached) yes
checking whether gcc supports -Wold-style-definition... (cached) yes
checking whether gcc supports -Wmissing-format-attribute... (cached) yes
checking whether gcc supports -Wno-overlength-strings... (cached) no
checking whether gcc supports -pedantic -Wno-long-long... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for egrep... (cached) grep -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stddef.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for strings.h... (cached) yes
checking for unistd.h... (cached) yes
checking for fcntl.h... (cached) yes
checking for sys/file.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for clearerr_unlocked... (cached) yes
checking for feof_unlocked... (cached) yes
checking for ferror_unlocked... (cached) yes
checking for fflush_unlocked... (cached) yes
checking for fgetc_unlocked... (cached) yes
checking for fgets_unlocked... (cached) yes
checking for fileno_unlocked... (cached) yes
checking for fprintf_unlocked... (cached) no
checking for fputc_unlocked... (cached) yes
checking for fputs_unlocked... (cached) yes
checking for fread_unlocked... (cached) yes
checking for fwrite_unlocked... (cached) yes
checking for getchar_unlocked... (cached) yes
checking for getc_unlocked... (cached) yes
checking for putchar_unlocked... (cached) yes
checking for putc_unlocked... (cached) yes
checking whether abort is declared... (cached) yes
checking whether asprintf is declared... (cached) no
checking whether basename is declared... (cached) no
checking whether errno is declared... (cached) no
checking whether vasprintf is declared... (cached) no
checking whether clearerr_unlocked is declared... (cached) yes
checking whether feof_unlocked is declared... (cached) yes
checking whether ferror_unlocked is declared... (cached) yes
checking whether fflush_unlocked is declared... (cached) yes
checking whether fgetc_unlocked is declared... (cached) yes
checking whether fgets_unlocked is declared... (cached) no
checking whether fileno_unlocked is declared... (cached) yes
checking whether fprintf_unlocked is declared... (cached) no
checking whether fputc_unlocked is declared... (cached) yes
checking whether fputs_unlocked is declared... (cached) no
checking whether fread_unlocked is declared... (cached) yes
checking whether fwrite_unlocked is declared... (cached) yes
checking whether getchar_unlocked is declared... (cached) yes
checking whether getc_unlocked is declared... (cached) yes
checking whether putchar_unlocked is declared... (cached) yes
checking whether putc_unlocked is declared... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking for sys/mman.h... (cached) yes
checking for mmap... (cached) yes
checking whether read-only mmap of a plain file works... (cached) yes
checking whether mmap from /dev/zero works... (cached) yes
checking for MAP_ANON(YMOUS)... (cached) yes
checking whether mmap with MAP_ANON(YMOUS) works... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkheaders.almost
config.status: creating config.h
config.status: config.h is unchanged
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/fixincludes'
srcdir="../.././fixincludes" /bin/sh ../.././fixincludes/mkfixinc.sh i686-pc-linux-gnu
sed -e 's/@gcc_version@/4.2.0/' < mkheaders.almost > mkheadersT
mv -f mkheadersT mkheaders
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/build-i686-pc-linux-gnu/fixincludes'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/zlib'
true "AR_FLAGS=rc" "CC_FOR_BUILD=gcc" "CFLAGS=-g -fkeep-inline-functions" "CXXFLAGS=-g -O2" "CFLAGS_FOR_BUILD=-g -O2" "CFLAGS_FOR_TARGET=-O2 -g -O2 " "INSTALL=/usr/bin/install -c" "INSTALL_DATA=/usr/bin/install -c -m 644" "INSTALL_PROGRAM=/usr/bin/install -c" "INSTALL_SCRIPT=/usr/bin/install -c" "LDFLAGS=" "LIBCFLAGS=-g -fkeep-inline-functions" "LIBCFLAGS_FOR_TARGET=-O2 -g -O2 " "MAKE=make" "MAKEINFO=/home/owner/Desktop/gcc-4.2-20070110/missing makeinfo --split-size=5000000 --split-size=5000000 --split-size=5000000 " "PICFLAG=" "PICFLAG_FOR_TARGET=" "SHELL=/bin/sh" "EXPECT=expect" "RUNTEST=runtest" "RUNTESTFLAGS=" "exec_prefix=/usr/local" "infodir=/usr/local/info" "libdir=/usr/local/lib" "prefix=/usr/local" "tooldir=/usr/local/i686-pc-linux-gnu" "AR=ar" "AS=as" "CC=gcc" "CXX=c++" "LD=ld" "LIBCFLAGS=-g -fkeep-inline-functions" "NM=nm" "PICFLAG=" "RANLIB=ranlib" "DESTDIR=" DO=all multi-do # make
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/zlib'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libcpp'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libcpp'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libdecnumber'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/libdecnumber'
make[3]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/gcc'
/home/owner/Desktop/gcc-4.2-20070110/missing flex  -ogengtype-lex.c ../.././gcc/gengtype-lex.l
WARNING: `flex' is missing on your system.  You should only need it if
         you modified a `.l' file.  You may need the `Flex' package
         in order for those modifications to take effect.  You can get
         `Flex' from any GNU archive site.
/home/owner/Desktop/gcc-4.2-20070110/missing bison  -d -o gengtype-yacc.c ../.././gcc/gengtype-yacc.y
WARNING: `bison' missing on your system.  You should only need it if
         you modified a `.y' file.  You may need the `Bison' package
         in order for those modifications to take effect.  You can get
         `Bison' from any GNU archive site.
gcc -c   -g -fkeep-inline-functions -DIN_GCC   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition -Wmissing-format-attribute -fno-common -Wno-error  -DHAVE_CONFIG_H -DGENERATOR_FILE -I. -Ibuild -I../.././gcc -I../.././gcc/build -I../.././gcc/../include -I../.././gcc/../libcpp/include  -I../.././gcc/../libdecnumber -I../libdecnumber    -o build/gengtype-lex.o gengtype-lex.c
gcc: gengtype-lex.c: No such file or directory
gcc: no input files
make[3]: *** [build/gengtype-lex.o] Error 1
make[3]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110/host-i686-pc-linux-gnu/gcc'
make[2]: *** [all-stage1-gcc] Error 2
make[2]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make: *** [all] Error 2
owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ sudo make install
Password:
make[1]: Entering directory `/home/owner/Desktop/gcc-4.2-20070110'
/bin/sh ./mkinstalldirs /usr/local /usr/local
/bin/sh: line 3: cd: host-i686-pc-linux-gnu/fixincludes: No such file or directory
make[1]: *** [install-fixincludes] Error 1
make[1]: Leaving directory `/home/owner/Desktop/gcc-4.2-20070110'
make: *** [install] Error 2
owner@owner-desktop:~/Desktop/gcc-4.2-20070110$


-------------------
I don't know the problem, can someone plese assist me?

---

### Post by majoridiot on 2007-01-16
> **Stomstedt said:**
> 
WARNING: `bison' missing on your system.  You should only need it if
         you modified a `.y' file.  You may need the `Bison' package
         in order for those modifications to take effect.  You can get
         `Bison' from any GNU archive site...

do you have bison installed?

---

### Post by Stomstedt on 2007-01-16
No, I don't have bison installed but I just did sudo apt-get install bison and also for flex as well.  It still doesn't seem to be working.. :???:

---

### Post by Stomstedt on 2007-01-16
When I installed bison and flex, it seems to still say I don't have it, when i try to make gcc again :(

---

### Post by Enverex on 2007-01-16
You probably need the -dev packages, not the normal ones.

---

### Post by Stomstedt on 2007-01-16
> **Enverex said:**
> You probably need the -dev packages, not the normal ones.

Where can you get such a thing?

---

### Post by majoridiot on 2007-01-16
4.2.0 is not an official release yet, so what you have might be incomplete or missing needed
dependencies.

is there a reason you can't use the latest gcc 4.0.3 stable from the ubuntu repositories?

---

### Post by Stomstedt on 2007-01-16
> **majoridiot said:**
> 4.2.0 is not an official release yet, so what you have might be incomplete or missing needed
dependencies.

is there a reason you can't use the latest gcc 4.0.3 stable from the ubuntu repositories?

I am attempting to run a program that says it requires gcc 4.2.0 or later.  Here is the error from the program:

> owner@owner-desktop:~/Desktop/gcc-4.2-20070110$ graalexe
/usr/bin/graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/graal)


---

### Post by gcordoba on 2007-02-23
and parallel programing which requires to enable the -fopenmp option which it is only available under gcc 4.2
  

Gustavo

---

### Post by hone on 2007-03-05
when I did a make dist clean and reconfigured it and ran a make after installing bison and flex it seemed to work.

---

