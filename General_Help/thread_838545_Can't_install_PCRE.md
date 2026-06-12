---
title: "Can't install PCRE"
date: 2008-06-23
forum: General Help
---

### Post by Sam324 on 2008-06-23
OK, so I tried to install the music plugin for Pidgin, which requires PCRE.  I downloaded and unzipped the archive.  I tried to compile it, and got:
```
sam@sam-ubuntu:~$ cd Desktop/pcre-7.7
sam@sam-ubuntu:~/Desktop/pcre-7.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking for ANSI C header files... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for strtoq... yes
checking for long long... yes
checking for unsigned long long... yes
checking for bcopy... yes
checking for memmove... yes
checking for strerror... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzopen in -lz... yes
checking bzlib.h usability... no
checking bzlib.h presence... no
checking for bzlib.h... no
checking for BZ2_bzopen in -lbz2... no
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
checking readline/history.h usability... no
checking readline/history.h presence... no
checking for readline/history.h... no
checking for readline in -lreadline... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libpcre.pc
config.status: creating libpcrecpp.pc
config.status: creating pcre-config
config.status: creating pcre.h
config.status: creating pcre_stringpiece.h
config.status: creating pcrecpparg.h
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing script-chmod commands
config.status: executing delete-old-chartables commands

pcre-7.7 configuration summary:

    Install prefix .................. : /usr/local
    C preprocessor .................. : gcc -E
    C compiler ...................... : gcc
    C++ preprocessor ................ : 
    C++ compiler .................... : 
    Linker .......................... : /usr/bin/ld -m elf_x86_64
    C preprocessor flags ............ : 
    C compiler flags ................ : -O2
    C++ compiler flags .............. : 
    Linker flags .................... : 
    Extra libraries ................. : 

    Build C++ library ............... : yes
    Enable UTF-8 support ............ : no
    Unicode properties .............. : no
    Newline char/sequence ........... : lf
    \R matches only ANYCRLF ......... : no
    EBCDIC coding ................... : no
    Rebuild char tables ............. : no
    Use stack recursion ............. : yes
    POSIX mem threshold ............. : 10
    Internal link size .............. : 2
    Match limit ..................... : 10000000
    Match limit recursion ........... : MATCH_LIMIT
    Build shared libs ............... : yes
    Build static libs ............... : yes
    Link pcregrep with libz ......... : no
    Link pcregrep with libbz2 ....... : no
    Link pcretest with libreadline .. : no

sam@sam-ubuntu:~/Desktop/pcre-7.7$ make
make  all-am
make[1]: Entering directory `/home/sam/Desktop/pcre-7.7'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_compile.lo -MD -MP -MF .deps/pcre_compile.Tpo -c -o pcre_compile.lo pcre_compile.c
rm: cannot remove `.libs/pcre_compile.o': Permission denied
rm: cannot remove `.libs/pcre_compile.o': Permission denied
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_compile.lo -MD -MP -MF .deps/pcre_compile.Tpo -c pcre_compile.c  -fPIC -DPIC -o .libs/pcre_compile.o
Assembler messages:
Fatal error: can't create .libs/pcre_compile.o: Permission denied
make[1]: *** [pcre_compile.lo] Error 1
make[1]: Leaving directory `/home/sam/Desktop/pcre-7.7'
make: *** [all] Error 2
sam@sam-ubuntu:~/Desktop/pcre-7.7$ 

```
How do I install it?  What do these errors mean?:mad:

---

### Post by Zulu-Zeffir on 2008-06-23
Try running it with root privelages.
As far as the errors "Permission Denied" stands out to me.  Hence my suggestion.
Prefix your commands with sudo <command>
This allows you to run the commands with root privelages without actually being root.

---

### Post by Sam324 on 2008-06-23
Ok.  I ran it with sudo and got:
```
sam@sam-ubuntu:~/Desktop/pcre-7.7$ sudo make
[sudo] password for sam: 
make  all-am
make[1]: Entering directory `/home/sam/Desktop/pcre-7.7'
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_compile.lo -MD -MP -MF .deps/pcre_compile.Tpo -c -o pcre_compile.lo pcre_compile.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_compile.lo -MD -MP -MF .deps/pcre_compile.Tpo -c pcre_compile.c  -fPIC -DPIC -o .libs/pcre_compile.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_compile.lo -MD -MP -MF .deps/pcre_compile.Tpo -c pcre_compile.c -o pcre_compile.o >/dev/null 2>&1
mv -f .deps/pcre_compile.Tpo .deps/pcre_compile.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_config.lo -MD -MP -MF .deps/pcre_config.Tpo -c -o pcre_config.lo pcre_config.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_config.lo -MD -MP -MF .deps/pcre_config.Tpo -c pcre_config.c  -fPIC -DPIC -o .libs/pcre_config.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_config.lo -MD -MP -MF .deps/pcre_config.Tpo -c pcre_config.c -o pcre_config.o >/dev/null 2>&1
mv -f .deps/pcre_config.Tpo .deps/pcre_config.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_dfa_exec.lo -MD -MP -MF .deps/pcre_dfa_exec.Tpo -c -o pcre_dfa_exec.lo pcre_dfa_exec.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_dfa_exec.lo -MD -MP -MF .deps/pcre_dfa_exec.Tpo -c pcre_dfa_exec.c  -fPIC -DPIC -o .libs/pcre_dfa_exec.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_dfa_exec.lo -MD -MP -MF .deps/pcre_dfa_exec.Tpo -c pcre_dfa_exec.c -o pcre_dfa_exec.o >/dev/null 2>&1
mv -f .deps/pcre_dfa_exec.Tpo .deps/pcre_dfa_exec.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_exec.lo -MD -MP -MF .deps/pcre_exec.Tpo -c -o pcre_exec.lo pcre_exec.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_exec.lo -MD -MP -MF .deps/pcre_exec.Tpo -c pcre_exec.c  -fPIC -DPIC -o .libs/pcre_exec.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_exec.lo -MD -MP -MF .deps/pcre_exec.Tpo -c pcre_exec.c -o pcre_exec.o >/dev/null 2>&1
mv -f .deps/pcre_exec.Tpo .deps/pcre_exec.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_fullinfo.lo -MD -MP -MF .deps/pcre_fullinfo.Tpo -c -o pcre_fullinfo.lo pcre_fullinfo.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_fullinfo.lo -MD -MP -MF .deps/pcre_fullinfo.Tpo -c pcre_fullinfo.c  -fPIC -DPIC -o .libs/pcre_fullinfo.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_fullinfo.lo -MD -MP -MF .deps/pcre_fullinfo.Tpo -c pcre_fullinfo.c -o pcre_fullinfo.o >/dev/null 2>&1
mv -f .deps/pcre_fullinfo.Tpo .deps/pcre_fullinfo.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_get.lo -MD -MP -MF .deps/pcre_get.Tpo -c -o pcre_get.lo pcre_get.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_get.lo -MD -MP -MF .deps/pcre_get.Tpo -c pcre_get.c  -fPIC -DPIC -o .libs/pcre_get.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_get.lo -MD -MP -MF .deps/pcre_get.Tpo -c pcre_get.c -o pcre_get.o >/dev/null 2>&1
mv -f .deps/pcre_get.Tpo .deps/pcre_get.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_globals.lo -MD -MP -MF .deps/pcre_globals.Tpo -c -o pcre_globals.lo pcre_globals.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_globals.lo -MD -MP -MF .deps/pcre_globals.Tpo -c pcre_globals.c  -fPIC -DPIC -o .libs/pcre_globals.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_globals.lo -MD -MP -MF .deps/pcre_globals.Tpo -c pcre_globals.c -o pcre_globals.o >/dev/null 2>&1
mv -f .deps/pcre_globals.Tpo .deps/pcre_globals.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_info.lo -MD -MP -MF .deps/pcre_info.Tpo -c -o pcre_info.lo pcre_info.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_info.lo -MD -MP -MF .deps/pcre_info.Tpo -c pcre_info.c  -fPIC -DPIC -o .libs/pcre_info.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_info.lo -MD -MP -MF .deps/pcre_info.Tpo -c pcre_info.c -o pcre_info.o >/dev/null 2>&1
mv -f .deps/pcre_info.Tpo .deps/pcre_info.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_maketables.lo -MD -MP -MF .deps/pcre_maketables.Tpo -c -o pcre_maketables.lo pcre_maketables.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_maketables.lo -MD -MP -MF .deps/pcre_maketables.Tpo -c pcre_maketables.c  -fPIC -DPIC -o .libs/pcre_maketables.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_maketables.lo -MD -MP -MF .deps/pcre_maketables.Tpo -c pcre_maketables.c -o pcre_maketables.o >/dev/null 2>&1
mv -f .deps/pcre_maketables.Tpo .deps/pcre_maketables.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_newline.lo -MD -MP -MF .deps/pcre_newline.Tpo -c -o pcre_newline.lo pcre_newline.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_newline.lo -MD -MP -MF .deps/pcre_newline.Tpo -c pcre_newline.c  -fPIC -DPIC -o .libs/pcre_newline.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_newline.lo -MD -MP -MF .deps/pcre_newline.Tpo -c pcre_newline.c -o pcre_newline.o >/dev/null 2>&1
mv -f .deps/pcre_newline.Tpo .deps/pcre_newline.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_ord2utf8.lo -MD -MP -MF .deps/pcre_ord2utf8.Tpo -c -o pcre_ord2utf8.lo pcre_ord2utf8.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_ord2utf8.lo -MD -MP -MF .deps/pcre_ord2utf8.Tpo -c pcre_ord2utf8.c  -fPIC -DPIC -o .libs/pcre_ord2utf8.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_ord2utf8.lo -MD -MP -MF .deps/pcre_ord2utf8.Tpo -c pcre_ord2utf8.c -o pcre_ord2utf8.o >/dev/null 2>&1
mv -f .deps/pcre_ord2utf8.Tpo .deps/pcre_ord2utf8.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_refcount.lo -MD -MP -MF .deps/pcre_refcount.Tpo -c -o pcre_refcount.lo pcre_refcount.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_refcount.lo -MD -MP -MF .deps/pcre_refcount.Tpo -c pcre_refcount.c  -fPIC -DPIC -o .libs/pcre_refcount.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_refcount.lo -MD -MP -MF .deps/pcre_refcount.Tpo -c pcre_refcount.c -o pcre_refcount.o >/dev/null 2>&1
mv -f .deps/pcre_refcount.Tpo .deps/pcre_refcount.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_study.lo -MD -MP -MF .deps/pcre_study.Tpo -c -o pcre_study.lo pcre_study.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_study.lo -MD -MP -MF .deps/pcre_study.Tpo -c pcre_study.c  -fPIC -DPIC -o .libs/pcre_study.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_study.lo -MD -MP -MF .deps/pcre_study.Tpo -c pcre_study.c -o pcre_study.o >/dev/null 2>&1
mv -f .deps/pcre_study.Tpo .deps/pcre_study.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_tables.lo -MD -MP -MF .deps/pcre_tables.Tpo -c -o pcre_tables.lo pcre_tables.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_tables.lo -MD -MP -MF .deps/pcre_tables.Tpo -c pcre_tables.c  -fPIC -DPIC -o .libs/pcre_tables.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_tables.lo -MD -MP -MF .deps/pcre_tables.Tpo -c pcre_tables.c -o pcre_tables.o >/dev/null 2>&1
mv -f .deps/pcre_tables.Tpo .deps/pcre_tables.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_try_flipped.lo -MD -MP -MF .deps/pcre_try_flipped.Tpo -c -o pcre_try_flipped.lo pcre_try_flipped.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_try_flipped.lo -MD -MP -MF .deps/pcre_try_flipped.Tpo -c pcre_try_flipped.c  -fPIC -DPIC -o .libs/pcre_try_flipped.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_try_flipped.lo -MD -MP -MF .deps/pcre_try_flipped.Tpo -c pcre_try_flipped.c -o pcre_try_flipped.o >/dev/null 2>&1
mv -f .deps/pcre_try_flipped.Tpo .deps/pcre_try_flipped.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_ucp_searchfuncs.lo -MD -MP -MF .deps/pcre_ucp_searchfuncs.Tpo -c -o pcre_ucp_searchfuncs.lo pcre_ucp_searchfuncs.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_ucp_searchfuncs.lo -MD -MP -MF .deps/pcre_ucp_searchfuncs.Tpo -c pcre_ucp_searchfuncs.c  -fPIC -DPIC -o .libs/pcre_ucp_searchfuncs.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_ucp_searchfuncs.lo -MD -MP -MF .deps/pcre_ucp_searchfuncs.Tpo -c pcre_ucp_searchfuncs.c -o pcre_ucp_searchfuncs.o >/dev/null 2>&1
mv -f .deps/pcre_ucp_searchfuncs.Tpo .deps/pcre_ucp_searchfuncs.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_valid_utf8.lo -MD -MP -MF .deps/pcre_valid_utf8.Tpo -c -o pcre_valid_utf8.lo pcre_valid_utf8.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_valid_utf8.lo -MD -MP -MF .deps/pcre_valid_utf8.Tpo -c pcre_valid_utf8.c  -fPIC -DPIC -o .libs/pcre_valid_utf8.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_valid_utf8.lo -MD -MP -MF .deps/pcre_valid_utf8.Tpo -c pcre_valid_utf8.c -o pcre_valid_utf8.o >/dev/null 2>&1
mv -f .deps/pcre_valid_utf8.Tpo .deps/pcre_valid_utf8.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_version.lo -MD -MP -MF .deps/pcre_version.Tpo -c -o pcre_version.lo pcre_version.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_version.lo -MD -MP -MF .deps/pcre_version.Tpo -c pcre_version.c  -fPIC -DPIC -o .libs/pcre_version.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_version.lo -MD -MP -MF .deps/pcre_version.Tpo -c pcre_version.c -o pcre_version.o >/dev/null 2>&1
mv -f .deps/pcre_version.Tpo .deps/pcre_version.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_xclass.lo -MD -MP -MF .deps/pcre_xclass.Tpo -c -o pcre_xclass.lo pcre_xclass.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_xclass.lo -MD -MP -MF .deps/pcre_xclass.Tpo -c pcre_xclass.c  -fPIC -DPIC -o .libs/pcre_xclass.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_xclass.lo -MD -MP -MF .deps/pcre_xclass.Tpo -c pcre_xclass.c -o pcre_xclass.o >/dev/null 2>&1
mv -f .deps/pcre_xclass.Tpo .deps/pcre_xclass.Plo
rm -f pcre_chartables.c
ln -s ./pcre_chartables.c.dist pcre_chartables.c
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcre_chartables.lo -MD -MP -MF .deps/pcre_chartables.Tpo -c -o pcre_chartables.lo pcre_chartables.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_chartables.lo -MD -MP -MF .deps/pcre_chartables.Tpo -c pcre_chartables.c  -fPIC -DPIC -o .libs/pcre_chartables.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcre_chartables.lo -MD -MP -MF .deps/pcre_chartables.Tpo -c pcre_chartables.c -o pcre_chartables.o >/dev/null 2>&1
mv -f .deps/pcre_chartables.Tpo .deps/pcre_chartables.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -O2 -version-info 0:1:0  -o libpcre.la -rpath /usr/local/lib pcre_compile.lo pcre_config.lo pcre_dfa_exec.lo pcre_exec.lo pcre_fullinfo.lo pcre_get.lo pcre_globals.lo pcre_info.lo pcre_maketables.lo pcre_newline.lo pcre_ord2utf8.lo pcre_refcount.lo pcre_study.lo pcre_tables.lo pcre_try_flipped.lo pcre_ucp_searchfuncs.lo pcre_valid_utf8.lo pcre_version.lo pcre_xclass.lo pcre_chartables.lo  
rm -fr  .libs/libpcre.a .libs/libpcre.la .libs/libpcre.lai .libs/libpcre.so .libs/libpcre.so.0 .libs/libpcre.so.0.0.1
gcc -shared  .libs/pcre_compile.o .libs/pcre_config.o .libs/pcre_dfa_exec.o .libs/pcre_exec.o .libs/pcre_fullinfo.o .libs/pcre_get.o .libs/pcre_globals.o .libs/pcre_info.o .libs/pcre_maketables.o .libs/pcre_newline.o .libs/pcre_ord2utf8.o .libs/pcre_refcount.o .libs/pcre_study.o .libs/pcre_tables.o .libs/pcre_try_flipped.o .libs/pcre_ucp_searchfuncs.o .libs/pcre_valid_utf8.o .libs/pcre_version.o .libs/pcre_xclass.o .libs/pcre_chartables.o   -Wl,-soname -Wl,libpcre.so.0 -o .libs/libpcre.so.0.0.1
(cd .libs && rm -f libpcre.so.0 && ln -s libpcre.so.0.0.1 libpcre.so.0)
(cd .libs && rm -f libpcre.so && ln -s libpcre.so.0.0.1 libpcre.so)
ar cru .libs/libpcre.a  pcre_compile.o pcre_config.o pcre_dfa_exec.o pcre_exec.o pcre_fullinfo.o pcre_get.o pcre_globals.o pcre_info.o pcre_maketables.o pcre_newline.o pcre_ord2utf8.o pcre_refcount.o pcre_study.o pcre_tables.o pcre_try_flipped.o pcre_ucp_searchfuncs.o pcre_valid_utf8.o pcre_version.o pcre_xclass.o pcre_chartables.o
ranlib .libs/libpcre.a
creating libpcre.la
(cd .libs && rm -f libpcre.la && ln -s ../libpcre.la libpcre.la)
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.     -O2 -MT pcreposix.lo -MD -MP -MF .deps/pcreposix.Tpo -c -o pcreposix.lo pcreposix.c
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcreposix.lo -MD -MP -MF .deps/pcreposix.Tpo -c pcreposix.c  -fPIC -DPIC -o .libs/pcreposix.o
 gcc -DHAVE_CONFIG_H -I. -O2 -MT pcreposix.lo -MD -MP -MF .deps/pcreposix.Tpo -c pcreposix.c -o pcreposix.o >/dev/null 2>&1
mv -f .deps/pcreposix.Tpo .deps/pcreposix.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -O2 -version-info 0:0:0  -o libpcreposix.la -rpath /usr/local/lib pcreposix.lo libpcre.la 
rm -fr  .libs/libpcreposix.a .libs/libpcreposix.la .libs/libpcreposix.lai .libs/libpcreposix.so .libs/libpcreposix.so.0 .libs/libpcreposix.so.0.0.0
gcc -shared  .libs/pcreposix.o  -Wl,--rpath -Wl,/home/sam/Desktop/pcre-7.7/.libs ./.libs/libpcre.so  -Wl,-soname -Wl,libpcreposix.so.0 -o .libs/libpcreposix.so.0.0.0
(cd .libs && rm -f libpcreposix.so.0 && ln -s libpcreposix.so.0.0.0 libpcreposix.so.0)
(cd .libs && rm -f libpcreposix.so && ln -s libpcreposix.so.0.0.0 libpcreposix.so)
ar cru .libs/libpcreposix.a  pcreposix.o
ranlib .libs/libpcreposix.a
creating libpcreposix.la
(cd .libs && rm -f libpcreposix.la && ln -s ../libpcreposix.la libpcreposix.la)
source='pcrecpp.cc' object='pcrecpp.lo' libtool=yes \
    DEPDIR=.deps depmode=none /bin/bash ./depcomp \
    /bin/bash ./libtool --tag=CXX   --mode=compile  -DHAVE_CONFIG_H -I.      -c -o pcrecpp.lo pcrecpp.cc
libtool: ignoring unknown tag CXX
libtool: unrecognized option `-DHAVE_CONFIG_H'
Try `libtool --help' for more information.
make[1]: *** [pcrecpp.lo] Error 1
make[1]: Leaving directory `/home/sam/Desktop/pcre-7.7'
make: *** [all] Error 2
sam@sam-ubuntu:~/Desktop/pcre-7.7$ 

```

---

### Post by Zulu-Zeffir on 2008-06-24
See if this info helps you.
[http://ubuntuforums.org/showthread.php?t=488356]("http://ubuntuforums.org/showthread.php?t=488356")

---

### Post by soungcha on 2008-08-04
it seem you only have a c compiler but don't have c++ compiler.
please install c++ compiler on you linux server.

the best way is to use yum

yum install gcc-c++

---

### Post by Odolyte on 2012-06-20
Hi,

I had the same problem.

I installed gcc-c++ as you suggest @soungcha.

./configure went ok.
when typing make i have this message :
```
rm -f pcre_chartables.c
ln -s ./pcre_chartables.c.dist pcre_chartables.c
make  all-am
make[1]: entrant dans le répertoire « /usr/local/src/pcre-8.30 »
  CC     pcre_byte_order.lo
  CC     pcre_compile.lo
  CC     pcre_config.lo
  CC     pcre_dfa_exec.lo
  CC     pcre_exec.lo
  CC     pcre_fullinfo.lo
  CC     pcre_get.lo
  CC     pcre_globals.lo
  CC     pcre_jit_compile.lo
  CC     pcre_maketables.lo
  CC     pcre_newline.lo
  CC     pcre_ord2utf8.lo
  CC     pcre_refcount.lo
  CC     pcre_string_utils.lo
  CC     pcre_study.lo
  CC     pcre_tables.lo
  CC     pcre_ucd.lo
  CC     pcre_valid_utf8.lo
  CC     pcre_version.lo
  CC     pcre_xclass.lo
  CC     pcre_chartables.lo
  CCLD   libpcre.la
  CC     pcreposix.lo
  CCLD   libpcreposix.la
  CXX    pcrecpp.lo
libtool: compile: unrecognized option `-DHAVE_CONFIG_H'
libtool: compile: Try `libtool --help' for more information.
make[1]: *** [pcrecpp.lo] Error 1
make[1]: leaving folder « /usr/local/src/pcre-8.30 »
make: *** [all] Error 2
```

Sorry for my Linux incompetence, i'm new to Linux and have a lot of things to learn...

Thx for your help!

Odo.

---

### Post by oldos2er on 2012-06-20
Please start a new thread.

---

