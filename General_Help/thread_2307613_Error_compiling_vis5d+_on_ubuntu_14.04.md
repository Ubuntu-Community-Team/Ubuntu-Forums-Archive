---
title: "Error compiling vis5d+ on ubuntu 14.04"
date: 2015-12-26
forum: General Help
---

### Post by lightning_bolt6 on 2015-12-26
Happy holidays everyone!
I've been trying to compile and install vis5d+ for research in meteorology. However, I'm getting a bunch of warnings and error messages when I run make. I don't know what's causing this and I need some guidance over what to do.

Here's the output when I run ./configure in the vis5d+ directory.
```
checking for a BSD compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for mawk... mawk 
checking whether make sets ${MAKE}... yes 
checking for vendor's cc to be used instead of gcc... checking for cc... cc 
checking for C compiler default output... a.out 
checking whether the C compiler works... yes 
checking whether we are cross compiling... no 
checking for executable suffix...  
checking for object suffix... o 
checking whether we are using the GNU C compiler... yes 
checking whether cc accepts -g... yes 
checking for style of include used by make... GNU 
checking dependency style of cc... gcc3 
checking for g++... g++ 
checking whether we are using the GNU C++ compiler... yes 
checking whether g++ accepts -g... yes 
checking dependency style of g++... gcc3 
checking for a BSD compatible install... /usr/bin/install -c 
checking whether make sets ${MAKE}... (cached) yes 
checking whether ln -s works... yes 
checking build system type... x86_64-unknown-linux-gnu 
checking host system type... x86_64-unknown-linux-gnu 
checking for ld used by GCC... /usr/bin/ld 
checking if the linker (/usr/bin/ld) is GNU ld... yes 
checking for /usr/bin/ld option to reload object files... -r 
checking for BSD-compatible nm... /usr/bin/nm -B 
checking how to recognise dependant libraries... file_magic ELF [0-9][0-9]*-bit [LM]SB (shared object|dynamic lib ) 
checking command to parse /usr/bin/nm -B output... ok 
checking how to run the C preprocessor... cc -E 
checking for dlfcn.h... yes 
checking for file... /usr/bin/file 
checking for ranlib... ranlib 
checking for strip... strip 
checking for objdir... .libs 
checking for cc option to produce PIC... -fPIC 
checking if cc PIC flag -fPIC works... yes 
checking if cc static flag -static works... yes 
checking if cc supports -c -o file.o... yes 
checking if cc supports -c -o file.lo...  
checking if cc supports -fno-rtti -fno-exceptions... yes 
checking whether the linker (/usr/bin/ld) supports shared libraries... yes 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking if libtool supports shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
creating libtool 
checking for libintl.h... yes 
checking for ranlib... (cached) ranlib 
checking for strerror in -lcposix... no 
checking for ANSI C header files... yes 
checking for cc option to accept ANSI C... none needed 
checking for an ANSI C-conforming const... yes 
checking for inline... inline 
checking for sys/types.h... yes 
checking for sys/stat.h... yes 
checking for stdlib.h... yes 
checking for string.h... yes 
checking for memory.h... yes 
checking for strings.h... yes 
checking for inttypes.h... yes 
checking for stdint.h... yes 
checking for unistd.h... yes 
checking for off_t... yes 
checking for size_t... yes 
checking for working alloca.h... yes 
checking for alloca... yes 
checking for stdlib.h... (cached) yes 
checking for unistd.h... (cached) yes 
checking for getpagesize... yes 
checking for working mmap... yes 
checking whether we are using the GNU C Library 2.1 or newer... yes 
checking for argz.h... yes 
checking for limits.h... yes 
checking for locale.h... yes 
checking for nl_types.h... yes 
checking for malloc.h... yes 
checking for stddef.h... yes 
checking for stdlib.h... (cached) yes 
checking for string.h... (cached) yes 
checking for unistd.h... (cached) yes 
checking for sys/param.h... yes 
checking for feof_unlocked... yes 
checking for fgets_unlocked... yes 
checking for getcwd... yes 
checking for getegid... yes 
checking for geteuid... yes 
checking for getgid... yes 
checking for getuid... yes 
checking for mempcpy... yes 
checking for munmap... yes 
checking for putenv... yes 
checking for setenv... yes 
checking for setlocale... yes 
checking for stpcpy... yes 
checking for strchr... yes 
checking for strcasecmp... yes 
checking for strdup... yes 
checking for strtoul... yes 
checking for tsearch... yes 
checking for __argz_count... yes 
checking for __argz_stringify... yes 
checking for __argz_next... yes 
checking for iconv... yes 
checking for iconv declaration...  
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft); 
checking for nl_langinfo and CODESET... yes 
checking for LC_MESSAGES... yes 
checking whether NLS is requested... yes 
checking whether included gettext is requested... no 
checking for libintl.h... (cached) yes 
checking for GNU gettext in libc... yes 
checking for dcgettext... yes 
checking for msgfmt... /usr/bin/msgfmt 
checking for gmsgfmt... /usr/bin/msgfmt 
checking for xgettext... /usr/bin/xgettext 
checking for bison... bison 
checking version of bison... 3.0.2, ok 
checking for catalogs to be installed...  pt_BR es 
checking for db2html... ../missing db2html 
checking for db2dvi... ../missing db2dvi 
checking for db2ps... ../missing db2ps 
checking for db2pdf... ../missing db2pdf 
checking for db2rtf... ../missing db2rtf 
checking for convert... /usr/bin/convert 
checking for f77... no 
checking for xlf... no 
checking for xlf77... no 
checking for cf77... no 
checking for fl32... no 
checking for g77... no 
checking for fort77... no 
checking for f90... no 
checking for xlf90... no 
checking for g77... no 
checking for f77... no 
checking for xlf... no 
checking for cf77... no 
checking for cft77... no 
checking for frt... no 
checking for pgf77... no 
checking for fl32... no 
checking for af77... no 
checking for fort77... no 
checking for f90... no 
checking for xlf90... no 
checking for pgf90... no 
checking for epcf90... no 
checking for f95... no 
checking for fort... no 
checking for xlf95... no 
checking for lf95... no 
checking for g95... no 
checking for fc... no 
checking whether we are using the GNU Fortran 77 compiler... no 
checking whether  accepts -g... no 
configure: WARNING: didn't find any Fortran compiler 
checking whether we are using gcc 2.90 or later... yes 
******************************************************* 
*       Congratulations! You are running Linux.       * 
******************************************************* 
checking whether cc accepts -malign-double... yes 
checking whether cc accepts -O3 -fomit-frame-pointer -malign-double... yes 
checking for float... yes 
checking size of float... 4 
checking for int... yes 
checking size of int... 4 
checking for signed char... yes 
checking size of signed char... 1 
checking whether byte ordering is bigendian... no 
checking for sqrt in -lm... yes 
checking for strcasecmp... (cached) yes 
checking for strncasecmp... yes 
checking for strdup... (cached) yes 
checking for X... libraries , headers  
checking for gethostbyname... yes 
checking for connect... yes 
checking for remove... yes 
checking for shmat... yes 
checking for IceConnectionNumber in -lICE... yes 
checking for glBegin in -lGL... yes 
checking for gluProject in -lGLU... yes 
checking for GL/gl.h... yes 
checking for XMesaGetBackBuffer... no 
checking for dlopen in -ldl... yes 
checking for Tcl_Eval in -ltcl... no 
checking for setrlimit... yes 
checking for iopen in -limage... no 
checking for nc_inq_dimlen in -lnetcdf... no 
**************************************************** 
Didn't find the NetCDF library; irregular data features 
will be disabled.  You can download the NetCDF source 
code from the NetCDF home page: 
    http://www.unidata.ucar.edu/packages/netcdf/ 
and/or use --with-netcdf=<lib> to specify the location 
of libnetcdf.a. 
**************************************************** 
**************************************************** 
Didn't find the mixkit library; 
You can download the Mixkit source 
code from the Qslim home page: 
    http://graphics.cs.uiuc.edu/~garland/software/qslim.html 
and/or use --with-mixkit=<lib> to specify the location 
of libmix.a. 
**************************************************** 
checking for X11/Xm/MwmUtil.h... no 
checking for sys/types.h... (cached) yes 
checking for sys/prctl.h... yes 
checking for sys/sysmp.h... no 
checking for sysmp.h... no 
checking for sys/lock.h... no 
checking for sys/stat.h... (cached) yes 
checking for fcntl.h... yes 
configure: creating ./config.status 
config.status: creating gtk/gradients/Makefile 
config.status: creating gtk/Makefile 
config.status: creating intl/Makefile 
config.status: creating po/Makefile.in 
config.status: creating Makefile 
config.status: creating src/Makefile 
config.status: creating doc/Makefile 
config.status: creating lui5/Makefile 
config.status: creating util/Makefile 
config.status: creating config.h 
config.status: config.h is unchanged 
config.status: creating src/api-config.h 
config.status: src/api-config.h is unchanged 
config.status: creating po/POTFILES 
config.status: creating po/Makefile
```

Here's the output when I run make and get a bunch of warnings and error messages. The most common warning I'm getting is: warning: cast from pointer to integer of different size 
```
make  all-recursive 
make[1]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1' 
Making all in po 
make[2]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1/po' 
make[2]: Nothing to be done for `all'. 
make[2]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1/po' 
Making all in intl 
make[2]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1/intl' 
make[2]: Nothing to be done for `all'. 
make[2]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1/intl' 
Making all in lui5 
make[2]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1/lui5' 
make[2]: Nothing to be done for `all'. 
make[2]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1/lui5' 
Making all in src 
make[2]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1/src' 
make  all-am 
make[3]: Entering directory `/home/lightning/Downloads/vis5d+-1.2.1/src' 
source='api.c' object='api.lo' libtool=yes \ 
    depfile='.deps/api.Plo' tmpdepfile='.deps/api.TPlo' \ 
    depmode=gcc3 /bin/sh ../depcomp \ 
    /bin/sh ../libtool --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.. -I.     -O3 -fomit-frame-pointer -malign-double  -c -o api.lo `test -f api.c || echo './'`api.c 
rm -f .libs/api.lo 
cc -DHAVE_CONFIG_H -I. -I. -I.. -I. -O3 -fomit-frame-pointer -malign-double -c api.c -MT api.lo -MD -MP -MF .deps/api.TPlo  -fPIC -DPIC -o api.o 
In file included from api.c:89:0: 
misc.h:40:14: error: conflicting types for 'round' 
 extern float round( float x ); 
              ^ 
api.c: In function 'is_valid_dtx_ctx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1108:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("is_valid_dtx_ctx") 
    ^ 
api.c: In function 'vis5d_reset_display_timer': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1135:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_reset_display_timer") 
    ^ 
api.c: In function 'vis5d_get_display_timer': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1172:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_display_timer") 
    ^ 
api.c: In function 'vis5d_get_context_name': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1190:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_context_name") 
    ^ 
api.c: In function 'vis5d_set_display_group': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1273:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_display_group") 
    ^ 
api.c: In function 'vis5d_invalidate_isosurface': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1355:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_invalidate_isosurface"); 
   ^ 
api.c: In function 'vis5d_invalidate_hslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1364:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_invalidate_isosurface"); 
   ^ 
api.c: In function 'vis5d_invalidate_vslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1373:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_invalidate_vslice"); 
   ^ 
api.c: In function 'vis5d_invalidate_chslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1387:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_invalidate_chslice"); 
   ^ 
api.c: In function 'vis5d_invalidate_cvslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1396:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_invalidate_isosurface"); 
   ^ 
api.c: In function 'vis5d_invalidate_hwind': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1405:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_invalidate_hwind"); 
   ^ 
api.c: In function 'vis5d_invalidate_vwind': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1412:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_invalidate_vwind"); 
   ^ 
api.c: In function 'vis5d_invalidate_hstream': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1419:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_invalidate_hstream"); 
   ^ 
api.c: In function 'vis5d_invalidate_vstream': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1426:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_invalidate_vstream"); 
   ^ 
api.c: In function 'vis5d_get_display_group': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1454:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_display_group") 
    ^ 
api.c: In function 'add_ctx_index_to_dtx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1480:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("add_ctx_index_to_dtx") 
    ^ 
api.c: In function 'remove_ctx_index_from_dtx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:1507:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("remove_ctx_index_from_dtx") 
    ^ 
api.c: In function 'vis5d_assign_display_to_data': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:1543:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_assign_display_to_data") 
    ^ 
api.c:1603:64: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
  printf("adding dtx to ctx %d %d 0x%x\n",display_index, index, (unsigned int) dtx); 
                                                                ^ 
api.c: In function 'vis5d_reset_display_context': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:2059:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_reset_display_context") 
    ^ 
api.c: In function 'vis5d_map_3d_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:2208:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_map_3d_window"); 
    ^ 
api.c: In function 'vis5d_get_display_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:2236:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_display_window") 
    ^ 
api.c: In function 'vis5d_get_ctx_values': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:2439:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_values") 
    ^ 
api.c: In function 'vis5d_get_dtx_values': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:2511:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_values") 
    ^ 
api.c: In function 'vis5d_set_dtx_values': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:2690:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_dtx_values") 
    ^ 
api.c: In function 'vis5d_set_probe_vars': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:3255:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_probe_vars") 
    ^ 
api.c: In function 'vis5d_init_sndwindow': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3293:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_sndwindow"); 
    ^ 
api.c: In function 'vis5d_init_memory': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:3378:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_init_memory"); 
    ^ 
api.c: In function 'vis5d_init_samescale': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3391:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_samescale"); 
    ^ 
api.c: In function 'vis5d_init_box': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3407:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_box"); 
    ^ 
api.c: In function 'vis5d_make_box': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3419:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_box"); 
    ^ 
api.c: In function 'vis5d_init_log': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3450:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_log"); 
    ^ 
api.c: In function 'vis5d_get_log': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3492:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_log"); 
    ^ 
api.c: In function 'vis5d_get_map': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3535:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_map"); 
    ^ 
api.c: In function 'vis5d_init_topo_and_map_ctx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3546:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_topo_and_map_ctx"); 
    ^ 
api.c: In function 'vis5d_init_topo': 
api.c:3581:46: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
    printf("in c vis5d_init_topo Topo=0x%x\n",(unsigned int) dtx->topo);  
                                              ^ 
api.c: In function 'vis5d_get_topo': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3598:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_topo"); 
    ^ 
api.c: In function 'vis5d_init_clock': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3638:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_clock"); 
    ^ 
api.c: In function 'vis5d_init_texture': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3649:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_texture"); 
    ^ 
api.c: In function 'vis5d_get_texture': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3659:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_texture") 
    ^ 
api.c: In function 'vis5d_init_firstarea': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3669:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_firstarea"); 
    ^ 
api.c: In function 'vis5d_get_firstarea': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3679:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_firstarea") 
    ^ 
api.c: In function 'vis5d_init_sequence': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3688:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_sequence"); 
    ^ 
api.c: In function 'vis5d_get_sequence': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3698:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_sequence"); 
    ^ 
api.c: In function 'vis5d_init_projection': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3712:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_projection"); 
    ^ 
api.c: In function 'vis5d_init_vertical': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3734:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_init_vertical"); 
    ^ 
api.c: In function 'load_topo_and_map': 
api.c:3757:48: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
    printf("in c load_topo_and_map topo=0x%x\n",(unsigned int) dtx->topo);  
                                                ^ 
api.c: In function 'vis5d_initialize_stuff': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:3858:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_initialize_stuff") 
    ^ 
api.c: In function 'vis5d_init_data_end': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:3920:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_init_data_end"); 
    ^ 
api.c: In function 'vis5d_get_v5dfilename': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4129:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_v5dfilename") 
    ^ 
api.c: In function 'vis5d_open_gridfile': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4160:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_open_gridfile"); 
    ^ 
api.c: In function 'vis5d_get_levels': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4320:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_levels") 
    ^ 
api.c: In function 'vis5d_get_ctx_numtimes': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4330:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_numtimes") 
    ^ 
api.c: In function 'vis5d_get_dtx_numtimes': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4340:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_numtimes") 
    ^ 
api.c: In function 'vis5d_get_ctx_time_stamp': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4362:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_ctx_time_stamp") 
   ^ 
api.c: In function 'vis5d_get_dtx_time_stamp': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4381:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_time_stamp") 
    ^ 
api.c: In function 'vis5d_set_ctx_time_stamp': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4405:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_set_ctx_time_stamp") 
   ^ 
api.c: In function 'vis5d_set_probe_on_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4444:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_probe_on_traj") 
    ^ 
api.c: In function 'vis5d_set_dtx_timestep': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4498:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_dtx_timestep") 
    ^ 
api.c: In function 'vis5d_get_ctx_timestep': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4546:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_timestep") 
    ^ 
api.c: In function 'vis5d_get_itx_timestep': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:4553:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_itx_timestep") 
    ^ 
api.c: In function 'vis5d_get_dtx_timestep': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4564:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_timestep") 
    ^ 
api.c: In function 'vis5d_set_hclip': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4590:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_hclip") 
    ^ 
api.c: In function 'vis5d_get_hclip': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4619:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_hclip") 
    ^ 
api.c: In function 'vis5d_set_vclip': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4633:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_vclip") 
    ^ 
api.c: In function 'vis5d_get_vclip': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4681:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_vclip") 
    ^ 
api.c: In function 'vis5d_set_clip_mode': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4692:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_current_clip") 
    ^ 
api.c: In function 'vis5d_get_clip_mode': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4704:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_current_clip") 
    ^ 
api.c: In function 'vis5d_get_ctx_numvars': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4726:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_numvars"); 
    ^ 
api.c: In function 'vis5d_find_var': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4746:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_find_var"); 
    ^ 
api.c: In function 'vis5d_get_ctx_var_name': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4762:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_var_name"); 
    ^ 
api.c: In function 'vis5d_get_var_units': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4778:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_var_units"); 
    ^ 
api.c: In function 'vis5d_get_var_type': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4804:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_var_name"); 
    ^ 
api.c: In function 'vis5d_get_var_info': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4821:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_var_info"); 
    ^ 
api.c: In function 'vis5d_get_ctx_var_range': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4848:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_ctx_var_range") 
   ^ 
api.c: In function 'vis5d_set_var_range': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:4866:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_var_range") 
    ^ 
api.c: In function 'vis5d_set_sound_vars': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:4919:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_sound_vars") 
    ^ 
api.c: In function 'vis5d_get_sound_vars': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5022:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_sound_vars") 
    ^ 
api.c: In function 'vis5d_set_wind_vars': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5089:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_wind_vars") 
    ^ 
api.c: In function 'vis5d_get_wind_vars': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5259:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_wind_vars") 
    ^ 
api.c: In function 'vis5d_reset_var_graphics': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5287:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_reset_var_graphics") 
   ^ 
api.c: In function 'vis5d_get_sizePRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5370:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_sizePRIME") 
   ^ 
api.c: In function 'vis5d_get_size': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5385:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_size") 
   ^ 
api.c: In function 'vis5d_get_grid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5408:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_grid"); 
    ^ 
api.c: In function 'vis5d_put_grid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5425:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_put_grid"); 
    ^ 
api.c: In function 'vis5d_get_grid_value': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5443:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_grid_value"); 
    ^ 
api.c: In function 'vis5d_verylarge_mode': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5468:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_verylarge_mode"); 
   ^ 
api.c: In function 'vis5d_get_ctx_projection': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5495:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_projection"); 
    ^ 
api.c: In function 'vis5d_get_dtx_projection': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5502:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_projection") 
    ^ 
api.c: In function 'vis5d_get_ctx_vertical': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5509:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_ctx_vertical"); 
    ^ 
api.c: In function 'vis5d_get_dtx_vertical': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5529:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_dtx_vertical"); 
    ^ 
api.c: In function 'vis5d_get_curved': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5549:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_size") 
   ^ 
api.c: In function 'vis5d_set_dtx_projection_and_vertsys': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5559:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_dtx_projection_and_vertsys") 
    ^ 
api.c: In function 'vis5d_load_topo_and_map': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5800:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_load_topo_and_map") 
   ^ 
api.c: In function 'vis5d_check_topo': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5808:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_check_topo") 
   ^ 
api.c: In function 'vis5d_check_map': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5816:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_check_map") 
   ^ 
api.c: In function 'vis5d_check_texture': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5824:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_check_texture") 
   ^ 
api.c: In function 'vis5d_get_topo_range': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5832:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_topo_range") 
   ^ 
api.c: In function 'vis5d_reset_topo_colors': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5841:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_reset_topo_colors"); 
   ^ 
api.c: In function 'vis5d_texture_image': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5870:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_texture"); 
    ^ 
api.c: In function 'vis5d_set_topo_color_var': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5878:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_topo_color_var"); 
    ^ 
api.c: In function 'vis5d_get_topo_color_var': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5894:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_topo_color_var") 
    ^ 
api.c: In function 'vis5d_make_clone_variable': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:5918:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_make_clone_variable") 
    ^ 
api.c: In function 'vis5d_compute_ext_func': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:5963:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_compute_ext_func") 
   ^ 
api.c: In function 'vis5d_make_expr_var': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6074:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_expr_var") 
    ^ 
api.c: In function 'vis5d_make_new_var': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:6107:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_make_new_var") 
    ^ 
api.c: In function 'vis5d_signal_redraw': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6127:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_signal_redraw") 
    ^ 
api.c: In function 'vis5d_check_redraw': 
api.c:6154:75: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in vis5d_check_redraw %d 0x%x\n",  index, (unsigned int) dtx);  
                                                                           ^ 
api.c: In function 'vis5d_signal_fastdraw': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6167:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_signal_fastdraw") 
    ^ 
api.c: In function 'vis5d_check_fastdraw': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6177:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_check_fastdraw"); 
    ^ 
api.c: In function 'vis5d_draw_frame': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6186:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_draw_frame"); 
    ^ 
api.c: In function 'vis5d_draw_3d_only': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6219:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_draw_3d_only"); 
    ^ 
api.c: In function 'vis5d_draw_2d_only': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6229:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_draw_2d_only"); 
    ^ 
api.c: In function 'vis5d_draw_sounding_only': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6237:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_draw_sounding_only"); 
    ^ 
api.c: In function 'vis5d_swap_frame': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6246:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_swap_frame"); 
    ^ 
api.c: In function 'vis5d_invalidate_dtx_frames': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6271:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_invalidate_dtx_frames") 
    ^ 
api.c: In function 'vis5d_set_pointer': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6284:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_pointer") 
   ^ 
api.c: In function 'vis5d_graphics_mode': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6310:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_graphics_mode"); 
   ^ 
api.c: In function 'vis5d_check_ctx_volume': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:6453:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_check_ctx_volume")  
    ^ 
api.c: In function 'vis5d_check_dtx_volume': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6460:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_check_dtx_volume") 
    ^ 
api.c: In function 'vis5d_var_graphics_options': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:6468:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_var_graphics_options"); 
   ^ 
api.c: In function 'vis5d_enable_graphics': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:6590:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_enable_graphics"); 
   ^ 
api.c: In function 'vis5d_get_volume': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6712:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_volume") 
    ^ 
api.c: In function 'vis5d_set_volume': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6721:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_volume") 
    ^ 
api.c: In function 'get_graphics_color_address': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6754:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("get_graphics_color_address") 
   ^ 
api.c: In function 'vis5d_set_cursor_color': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6896:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_cursor_color") 
   ^ 
api.c: In function 'vis5d_get_color_table_address': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6926:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_color_table_address") 
   ^ 
api.c: In function 'vis5d_get_color_table_params': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:6983:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_color_table_params") 
    ^ 
api.c: In function 'vis5d_load_color_table': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7028:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_load_color_table") 
    ^ 
api.c: In function 'vis5d_set_color_table_params': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7085:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_color_table_params") 
   ^ 
api.c: In function 'vis5d_alpha_mode': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7251:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_alpha_mode"); 
    ^ 
api.c: In function 'vis5d_set_font': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7260:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_font"); 
   ^ 
api.c: In function 'vis5d_font': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7279:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_font"); 
    ^ 
api.c: In function 'vis5d_soundfont': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7287:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_soundfont"); 
    ^ 
api.c: In function 'vis5d_get_font': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7312:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_font"); 
    ^ 
api.c: In function 'vis5d_resize_contour_font': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7324:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_resize_contour_font"); 
    ^ 
api.c: In function 'vis5d_get_font_height': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7337:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_font"); 
    ^ 
api.c: In function 'vis5d_linewidth': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7360:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_linewidth"); 
    ^ 
api.c: In function 'vis5d_get_linewidth': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7367:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_linewidth"); 
    ^ 
api.c: In function 'vis5d_gl_setup': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7377:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_gl_init"); 
    ^ 
api.c: In function 'vis5d_set_matrix': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7388:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_matrix") 
    ^ 
api.c: In function 'vis5d_get_matrix': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7399:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_matrix") 
   ^ 
api.c: In function 'vis5d_matrix_mult': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7408:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_matrix") 
   ^ 
api.c: In function 'vis5d_set_ortho_view': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7426:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_ortho_view") 
    ^ 
api.c: In function 'vis5d_set_view': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7470:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_view") 
    ^ 
api.c: In function 'vis5d_get_view': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7486:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_view") 
    ^ 
api.c: In function 'vis5d_set_camera': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7498:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_camera"); 
    ^ 
api.c: In function 'vis5d_get_camera': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7518:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_camera"); 
    ^ 
api.c: In function 'vis5d_get_box_bounds': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:7532:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_box_bounds"); 
    ^ 
api.c: In function 'vis5d_make_isosurface': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7557:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_make_iso_surface") 
    ^ 
api.c: In function 'vis5d_set_isosurface': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7571:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_iso_surface") 
    ^ 
api.c: In function 'vis5d_get_isosurface': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7579:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_iso_surface") 
   ^ 
api.c: In function 'vis5d_get_isosurface_color_var': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7590:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_isosurface_color_var"); 
    ^ 
api.c: In function 'vis5d_set_isosurface_color_var': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:7603:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_isosurface_color_var"); 
    ^ 
api.c: In function 'new_slice_pos': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8323:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_new_slice_pos") 
   ^ 
api.c: In function 'vis5d_make_hslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8399:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_make_hslice") 
   ^ 
api.c: In function 'vis5d_set_hslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8420:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_hslice") 
    ^ 
api.c: In function 'vis5d_get_hslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8453:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_hslice") 
   ^ 
api.c: In function 'vis5d_make_vslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8472:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_make_vslice") 
   ^ 
api.c: In function 'vis5d_set_vslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8493:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_vslice") 
    ^ 
api.c: In function 'vis5d_get_vslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8512:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_vslice") 
   ^ 
api.c: In function 'vis5d_make_chslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8533:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_make_chslice") 
    ^ 
api.c: In function 'vis5d_set_chslice_limits': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8550:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_set_chslice") 
   ^ 
api.c: In function 'vis5d_set_chslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8574:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_chslice") 
    ^ 
api.c: In function 'vis5d_get_chslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8598:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_chslice") 
   ^ 
api.c: In function 'vis5d_get_chslice_limits': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8608:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_get_chslice") 
   ^ 
api.c: In function 'vis5d_make_cvslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8629:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_make_cvslice") 
   ^ 
api.c: In function 'vis5d_set_cvslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8649:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_cvslice") 
    ^ 
api.c: In function 'vis5d_get_cvslice': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:8665:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_get_cvslice") 
    ^ 
api.c: In function 'vis5d_make_hwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8685:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_hwindslice") 
    ^ 
api.c: In function 'vis5d_set_hwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8711:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_hwindslice") 
    ^ 
api.c: In function 'vis5d_get_hwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8768:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_hwindslice") 
   ^ 
api.c: In function 'vis5d_make_vwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8787:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_vwindslice") 
    ^ 
api.c: In function 'vis5d_set_vwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8811:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_vwindslice") 
    ^ 
api.c: In function 'vis5d_get_vwindslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8829:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_vwindslice") 
    ^ 
api.c: In function 'vis5d_make_hstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8851:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_hstreamslice") 
    ^ 
api.c: In function 'vis5d_set_hstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8874:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_hstreamslice") 
    ^ 
api.c: In function 'vis5d_get_hstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8886:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_hstreamslice") 
    ^ 
api.c: In function 'vis5d_make_vstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8904:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_vstreamslice") 
    ^ 
api.c: In function 'vis5d_set_vstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8929:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_vstreamslice") 
    ^ 
api.c: In function 'vis5d_get_vstreamslice': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8946:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_vstreamslice") 
    ^ 
api.c: In function 'vis5d_print_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:8963:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_print_traj") 
    ^ 
api.c: In function 'vis5d_make_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9025:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_traj") 
    ^ 
api.c: In function 'vis5d_set_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9053:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_traj") 
    ^ 
api.c: In function 'vis5d_get_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9064:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_traj") 
   ^ 
api.c: In function 'vis5d_set_trajectory_color_var': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9078:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_trajectory_color_var"); 
    ^ 
api.c: In function 'vis5d_get_trajectory_color_var': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9098:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_trajecotry_color_var"); 
    ^ 
api.c: In function 'vis5d_delete_last_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9107:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_del_traj"); 
   ^ 
api.c: In function 'vis5d_delete_traj_set': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9115:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_del_traj_set"); 
   ^ 
api.c: In function 'vis5d_get_num_traj': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9126:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_num_traj"); 
    ^ 
api.c: In function 'vis5d_get_traj_info': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9140:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_traj_info"); 
    ^ 
api.c: In function 'vis5d_make_timestep_graphics': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9165:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_timestep_graphics") 
    ^ 
api.c: In function 'vis5d_free_graphics': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9194:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_free_graphics") 
    ^ 
api.c: In function 'vis5d_make_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9265:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_make_label"); 
    ^ 
api.c: In function 'vis5d_new_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9289:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_new_label"); 
    ^ 
api.c: In function 'vis5d_edit_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9318:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_edit_label"); 
    ^ 
api.c: In function 'vis5d_find_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9363:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_find_label"); 
    ^ 
api.c: In function 'vis5d_move_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9384:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_move_label"); 
    ^ 
api.c: In function 'vis5d_delete_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9405:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_delete_label"); 
    ^ 
api.c: In function 'vis5d_get_label': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9439:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_label"); 
    ^ 
api.c: In function 'vis5d_set_cursor': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9475:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_cursor") 
    ^ 
api.c: In function 'vis5d_get_cursor': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9487:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_cursor") 
    ^ 
api.c: In function 'vis5d_set_logo_size': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9497:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_logo_size") 
    ^ 
api.c: In function 'vis5d_set_legends': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9507:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_legends") 
   ^ 
api.c: In function 'vis5d_get_legends': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9522:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_legends") 
   ^ 
api.c: In function 'vis5d_get_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9535:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_window"); 
    ^ 
api.c: In function 'vis5d_resize_3d_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9571:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_resize_3d_window"); 
    ^ 
api.c: In function 'vis5d_moveresize_3d_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9607:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_moveresize_3d_window") 
    ^ 
api.c: In function 'vis5d_resize_sounding_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9627:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_resize_sounding_window") 
    ^ 
api.c: In function 'vis5d_save_to_v5dfile': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9689:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_save_to_v5dfile") 
    ^ 
api.c: In function 'vis5d_print_snd_window': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9710:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_print_snd_window") 
    ^ 
api.c: In function 'vis5d_project': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9780:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_project") 
   ^ 
api.c: In function 'vis5d_unproject': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9790:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_unproject") 
   ^ 
api.c: In function 'vis5d_xyzPRIME_to_gridPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9800:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_xyzPRIME_to_gridPRIME") 
   ^ 
api.c: In function 'vis5d_xyz_to_grid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9809:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_xyz_to_grid") 
   ^ 
api.c: In function 'vis5d_gridPRIME_to_xyzPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9820:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_gridPRIME_to_xyzPRIME") 
   ^ 
api.c: In function 'vis5d_gridPRIME_to_grid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9833:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_gridPRIME_to_grid") 
    ^ 
api.c: In function 'vis5d_grid_to_gridPRIME': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9846:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_grid_to_gridPRIME") 
    ^ 
api.c: In function 'vis5d_grid_to_xyz': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9860:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_grid_to_xyz") 
   ^ 
api.c: In function 'vis5d_xyzPRIME_to_geo': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9873:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_xyzPRIME_to_geo") 
   ^ 
api.c: In function 'vis5d_geo_to_xyzPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9883:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_geo_to_xyzPRIME") 
    ^ 
api.c: In function 'vis5d_xyz_to_geo': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9897:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_xyz_to_grid") 
   ^ 
api.c: In function 'vis5d_rowcol_to_latlon': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9908:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_rowcol_to_latlon") 
    ^ 
api.c: In function 'vis5d_rowcolPRIME_to_latlon': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9917:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_rowcolPRIME_to_latlon") 
    ^ 
api.c: In function 'vis5d_grid_to_geo': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9929:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_grid_to_geo") 
    ^ 
api.c: In function 'vis5d_gridPRIME_to_geo': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9943:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_gridPRIME_to_geo") 
    ^ 
api.c: In function 'vis5d_latlon_to_rowcol': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9955:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_latlon_to_rowcol") 
    ^ 
api.c: In function 'vis5d_latlon_to_rowcolPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9965:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_latlon_to_rowcolPRIME") 
    ^ 
api.c: In function 'vis5d_geo_to_grid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:9976:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_geo_to_grid") 
    ^ 
api.c: In function 'vis5d_geo_to_gridPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:9989:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_geo_to_gridPRIME") 
    ^ 
api.c: In function 'vis5d_gridlevelPRIME_to_height': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10000:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_gridlevelPRIME_to_height") 
    ^ 
api.c: In function 'vis5d_gridlevel_to_height': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10009:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_gridlevel_to_height") 
    ^ 
api.c: In function 'vis5d_gridlevel_to_pressure': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10017:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_gridlevel_to_pressure") 
    ^ 
api.c: In function 'vis5d_height_to_gridlevelPRIME': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10025:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_height_to_gridlevelPRIME") 
    ^ 
api.c: In function 'vis5d_height_to_gridlevel': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10034:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_height_to_gridlevel") 
    ^ 
api.c: In function 'vis5d_geo_to_xyz': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10045:3: note: in expansion of macro 'CONTEXT' 
   CONTEXT("vis5d_geo_to_xyz") 
   ^ 
api.c: In function 'vis5d_restore': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10083:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_restore") 
    ^ 
api.c: In function 'vis5d_set_user_data_flag': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10097:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_user_data_flag") 
    ^ 
api.c: In function 'vis5d_set_user_flags': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10111:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_user_flags") 
    ^ 
api.c: In function 'vis5d_set_topo_base': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10124:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_topo_base") 
    ^ 
api.c: In function 'vis5d_get_flatmap_level': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10139:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_flatmap_level") 
    ^ 
api.c: In function 'vis5d_set_flatmap_level': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10157:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_flatmap_level") 
    ^ 
api.c: In function 'vis5d_init_cloned_var_colortables': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10175:5: note: in expansion of macro 'DPY_CONTEXT' 
     DPY_CONTEXT("vis5d_init_cloned_var_colortables"); 
     ^ 
api.c: In function 'vis5d_enable_sfc_map': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10254:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_enable_sfc_map") 
    ^ 
api.c: In function 'vis5d_enable_sfc_graphics': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10305:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_enable_sfc_graphics") 
    ^ 
api.c: In function 'vis5d_get_view_scales': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10417:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_view_scales") 
    ^ 
api.c: In function 'vis5d_set_view_scales': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10452:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_view_scales") 
    ^ 
api.c: In function 'vis5d_get_vert_exaggeration': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10494:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_get_vert_exaggeration") 
    ^ 
api.c: In function 'vis5d_set_vert_exaggeration': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10564:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_set_vert_exaggeration") 
    ^ 
api.c: In function 'vis5d_set_all_invalid': 
api.c:245:53: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad context in %s %d 0x%x\n", msg,index,(unsigned int) ctx); \ 
                                                     ^ 
api.c:10588:4: note: in expansion of macro 'CONTEXT' 
    CONTEXT("vis5d_set_all_invalid") 
    ^ 
api.c: In function 'vis5d_set_all_irregular_invalid': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:10626:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_set_all_irregular_invalid"); 
    ^ 
api.c: In function 'add_itx_index_to_dtx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10646:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("add_itx_index_to_dtx") 
    ^ 
api.c: In function 'remove_itx_index_from_dtx': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:10665:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("remove_itx_index_from_dtx") 
    ^ 
api.c: In function 'vis5d_assign_display_to_irregular_data': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:10691:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_assign_display_to_irregular_data") 
    ^ 
api.c: In function 'vis5d_get_itx_numtimes': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:10995:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_itx_numtimes") 
    ^ 
api.c: In function 'vis5d_get_itx_time_stamp': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11002:3: note: in expansion of macro 'IRG_CONTEXT' 
   IRG_CONTEXT("vis5d_get_itx_time_stamp") 
   ^ 
api.c: In function 'vis5d_get_itx_var_name': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11015:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_itx_var_name"); 
    ^ 
api.c: In function 'vis5d_get_itx_name': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11028:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_itx_file_name"); 
    ^ 
api.c: In function 'vis5d_get_itx_numvars': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11036:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_itx_numvars"); 
    ^ 
api.c: In function 'vis5d_set_text_plot': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11050:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_set_text_plot_var"); 
    ^ 
api.c: In function 'vis5d_get_text_plot': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11070:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_get_text_plot_var"); 
    ^ 
api.c: In function 'vis5d_get_itx_var_range': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11127:3: note: in expansion of macro 'IRG_CONTEXT' 
   IRG_CONTEXT("vis5d_get_itx_var_range") 
   ^ 
api.c: In function 'vis5d_enable_irregular_graphics': 
api.c:263:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad irregular context in %s %d 0x%x\n", msg,index,(unsigned int) itx); \ 
                                                               ^ 
api.c:11154:4: note: in expansion of macro 'IRG_CONTEXT' 
    IRG_CONTEXT("vis5d_enable_irregular_graphics"); 
    ^ 
api.c: In function 'vis5d_save_scene': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11272:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_save_scene"); 
    ^ 
api.c: In function 'vis5d_stereo_enabled': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11289:5: note: in expansion of macro 'DPY_CONTEXT' 
     DPY_CONTEXT("vis5d_stereo_enabled") 
     ^ 
api.c: In function 'vis5d_stereo_set': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11297:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_stereo_off") 
    ^ 
api.c: In function 'vis5d_stereo_get': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11322:4: note: in expansion of macro 'DPY_CONTEXT' 
    DPY_CONTEXT("vis5d_stereo_get") 
    ^ 
api.c: In function 'vis5d_set_maxtmesh': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11412:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_maxtmesh") 
   ^ 
api.c: In function 'vis5d_get_maxtmesh': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11419:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_maxtmesh") 
   ^ 
api.c: In function 'vis5d_set_vstride': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11426:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_set_vstride") 
   ^ 
api.c: In function 'vis5d_get_vstride': 
api.c:253:63: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast] 
     printf("bad display_context in %s %d 0x%x\n", msg, index, (unsigned int) dtx); \ 
                                                               ^ 
api.c:11434:3: note: in expansion of macro 'DPY_CONTEXT' 
   DPY_CONTEXT("vis5d_get_vstride") 
   ^ 
api.c: In function 'vis5d_load_color_table': 
api.c:7041:10: warning: ignoring return value of 'fscanf', declared with attribute warn_unused_result [-Wunused-result] 
    fscanf( f, "%d %f %f %f %f\n", &entries, &min, &max, 
          ^ 
api.c:7044:13: warning: ignoring return value of 'fscanf', declared with attribute warn_unused_result [-Wunused-result] 
       fscanf( f, "%d %d %d %d\n", &r[i], &g[i], &b[i], &a[i] ); 
             ^ 
make[3]: *** [api.lo] Error 1 
make[3]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1/src' 
make[2]: *** [all] Error 2 
make[2]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1/src' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/lightning/Downloads/vis5d+-1.2.1' 
make: *** [all] Error 2
```

---

### Post by mc4man on 2015-12-26
That source is 13+yrs. old, can't you find something more current to use?
(- odds of building now are practically nil

---

### Post by lightning_bolt6 on 2015-12-27
Ok, thank you. I found a way to install vis5d using a different source (I used vis5d 5.2 from ssec.wisc.edu, which actually isn't vis5d+ but it will get the job I need done).
 [ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/](ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/) 
There's the source for anyone who wants it- I had to download vis5d.linux.viewer.tar.Z, then uncompress and untar it inside the vis5d directory as well to make it work. Here's the readme file, which is also located in the link I just gave.
[ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/README](ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/README)

---

### Post by Jonathan_McKinney on 2016-05-18
> **lightning_bolt6 said:**
> Ok, thank you. I found a way to install vis5d using a different source (I used vis5d 5.2 from ssec.wisc.edu, which actually isn't vis5d+ but it will get the job I need done).
 [ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/](ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/) 
There's the source for anyone who wants it- I had to download vis5d.linux.viewer.tar.Z, then uncompress and untar it inside the vis5d directory as well to make it work. Here's the readme file, which is also located in the link I just gave.
[ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/README](ftp://ftp.ssec.wisc.edu/pub/vis5d-5.2/README)


Check out: [https://github.com/pseudotensor/Vis5dPlus/](https://github.com/pseudotensor/Vis5dPlus/) .  I enhanced vis5d+ from that source forge repo to deal with not only memory issues but also dealt with installation issues.  See the jonconfigure.sh .  You might be able to just run it, but look at it to be sure and run things step-by-step.  This handles all the odd compiler issues.  You may need some ubuntu packages.  This all works on the latest ubuntu.

---

