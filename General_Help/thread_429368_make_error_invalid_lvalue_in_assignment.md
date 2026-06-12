---
title: "make: error: invalid lvalue in assignment"
date: 2007-05-01
forum: General Help
---

### Post by adb2_aber on 2007-05-01
Hi all,

I'm attempting to make a file from [http://www.bodden.de/misc/ntfsrecovery/body_bad_sector_recovery_on_ntfs.php]("http://www.bodden.de/misc/ntfsrecovery/body_bad_sector_recovery_on_ntfs.php"), however am getting errors and it isn't working. I was wondering if anyone could help me to get this to work please?

./configure and make output is below, configure seems to be fine it's just the make!

Cheers

> andy@home:~/ntfs$ ./configure
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
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
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 gthread-2.0 gnome-vfs-module-2.0... configure: WARNING: Linux-NTFS Gnome VFS module requires glib-2.0 and gnome-vfs-module-2.0 libraries.
checking version of gcc... 4.1, ok
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking features.h usability... yes
checking features.h presence... yes
checking for features.h... yes
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking sys/endian.h usability... no
checking sys/endian.h presence... no
checking for sys/endian.h... no
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking for sys/stat.h... (cached) yes
checking for sys/types.h... (cached) yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking linux/major.h usability... yes
checking linux/major.h presence... yes
checking for linux/major.h... yes
checking linux/fd.h usability... yes
checking linux/fd.h presence... yes
checking for linux/fd.h... yes
checking machine/endian.h usability... no
checking machine/endian.h presence... no
checking for machine/endian.h... no
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for working long double with more range or precision than double... yes
checking for off_t... yes
checking for size_t... yes
checking for struct stat.st_blocks... yes
checking for struct stat.st_rdev... yes
checking for getmntent in -lsun... no
checking for getmntent in -lseq... no
checking for getmntent in -lgen... no
checking for getmntent... yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking whether mbrtowc and mbstate_t are properly declared... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking whether utime accepts a null argument... yes
checking for vprintf... yes
checking for _doprnt... no
checking for atexit... yes
checking for fdatasync... yes
checking for hasmntopt... yes
checking for memmove... yes
checking for memset... yes
checking for regcomp... yes
checking for setlocale... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strtol... yes
checking for strtoul... yes
checking for utime... yes
checking for mbsinit... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating include/Makefile
config.status: creating include/ntfs/Makefile
config.status: creating libntfs/Makefile
config.status: creating libntfs/libntfs.conf
config.status: creating libntfs/libntfs-gnomevfs.8
config.status: creating ntfsprogs/Makefile
config.status: creating ntfsprogs/mkntfs.8
config.status: creating ntfsprogs/ntfscat.8
config.status: creating ntfsprogs/ntfsclone.8
config.status: creating ntfsprogs/ntfscluster.8
config.status: creating ntfsprogs/ntfsfix.8
config.status: creating ntfsprogs/ntfsinfo.8
config.status: creating ntfsprogs/ntfslabel.8
config.status: creating ntfsprogs/ntfsls.8
config.status: creating ntfsprogs/ntfsprogs.8
config.status: creating ntfsprogs/ntfsresize.8
config.status: creating ntfsprogs/ntfsundelete.8
config.status: creating ntfsprogs.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

andy@home:~/ntfs$ make
make  all-recursive
make[1]: Entering directory `/home/andy/ntfs'
Making all in doc
make[2]: Entering directory `/home/andy/ntfs/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/andy/ntfs/doc'
Making all in include
make[2]: Entering directory `/home/andy/ntfs/include'
Making all in ntfs
make[3]: Entering directory `/home/andy/ntfs/include/ntfs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/andy/ntfs/include/ntfs'
make[3]: Entering directory `/home/andy/ntfs/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/andy/ntfs/include'
make[2]: Leaving directory `/home/andy/ntfs/include'
Making all in libntfs
make[2]: Entering directory `/home/andy/ntfs/libntfs'
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/ntfs     -g -O2 -Wall -fms-extensions -MT attrib.lo -MD -MP -MF ".deps/attrib.Tpo" \
          -c -o attrib.lo `test -f 'attrib.c' || echo './'`attrib.c; \
        then mv -f ".deps/attrib.Tpo" ".deps/attrib.Plo"; \
        else rm -f ".deps/attrib.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../include/ntfs -g -O2 -Wall -fms-extensions -MT attrib.lo -MD -MP -MF .deps/attrib.Tpo -c attrib.c  -fPIC -DPIC -o .libs/attrib.o
attrib.c: In function 'ntfs_attr_pread':
attrib.c:802: error: invalid lvalue in assignment
attrib.c:818: error: invalid lvalue in assignment
attrib.c: In function 'ntfs_attr_pwrite':
attrib.c:1059: error: invalid lvalue in assignment
attrib.c:1079: error: invalid lvalue in assignment
attrib.c: In function 'ntfs_attr_mst_pread':
attrib.c:1193: error: invalid lvalue in assignment
attrib.c: In function 'ntfs_external_attr_find':
attrib.c:1563: warning: pointer targets in assignment differ in signedness
attrib.c: In function 'ntfs_attr_make_non_resident':
attrib.c:2481: warning: pointer targets in passing argument 2 of 'ntfs_mapping_pairs_build' differ in signedness
attrib.c: In function 'ntfs_non_resident_attr_shrink':
attrib.c:2992: warning: pointer targets in passing argument 2 of 'ntfs_mapping_pairs_build' differ in signedness
make[2]: *** [attrib.lo] Error 1
make[2]: Leaving directory `/home/andy/ntfs/libntfs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andy/ntfs'
make: *** [all] Error 2


---

