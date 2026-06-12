---
title: "digikam 0.9.0-beta3 - compilation problem"
date: 2006-10-21
forum: General Help
---

### Post by Sir_Yaro on 2006-10-21
Hi. I'd like to ask for some help. For the first time i can't handle this by myself... :/ I don't have a clue how to fix compilation process. 
I'll give u length logs couse i'm not sure what is important and what is not.

```
[yaro][/tmp/digikam-0.9.0-beta3]$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr//lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr//bin/moc
checking for uic... /usr//bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for xmllint... /usr/bin/xmllint
checking for Qt docs... NO
checking for dot... not found
checking for doxygen... /usr/bin/doxygen
checking if hidden visibility should be enabled... no
checking for pkg-config... yes
checking for int... (cached) yes
checking size of int... (cached) 4
checking for short... (cached) yes
checking size of short... (cached) 2
checking for long... (cached) yes
checking size of long... (cached) 4
checking for char *... (cached) yes
checking size of char *... (cached) 4
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking for sqlite3 >= 3.0... yes
checking SQLITE_CFLAGS...
checking SQLITE_LIBS... -lsqlite3
checking lcms/lcms.h usability... no
checking lcms/lcms.h presence... no
checking for lcms/lcms.h... no
checking lcms.h usability... yes
checking lcms.h presence... yes
checking for lcms.h... yes
checking whether byte ordering is bigendian... (cached) no
checking for gphoto2-config... /usr/bin/gphoto2-config
checking for gphoto2-port-config... /usr/bin/gphoto2-port-config
checking for libkipi >= 0.1... yes
checking LIBKIPI_CFLAGS...
checking LIBKIPI_LIBS... -lkipi found
checking for TIFFWriteScanline in -ltiff... yes
checking tiffio.h usability... yes
checking tiffio.h presence... yes
checking for tiffio.h... yes
checking for png_set_add_alpha in -lpng... yes
checking exiv2/exif.hpp usability... no
checking exiv2/exif.hpp presence... yes
configure: WARNING: exiv2/exif.hpp: present but cannot be compiled
configure: WARNING: exiv2/exif.hpp:     check for missing prerequisite headers?
configure: WARNING: exiv2/exif.hpp: see the Autoconf documentation
configure: WARNING: exiv2/exif.hpp:     section "Present But Cannot Be Compiled"
configure: WARNING: exiv2/exif.hpp: proceeding with the preprocessor's result
configure: WARNING: exiv2/exif.hpp: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for exiv2/exif.hpp... yes
configure: creating ./config.status
fast creating digikam/utilities/hotplug/digikam-download.desktop
config.pl: fast created 1 file(s).
config.status: creating config.h
config.status: executing depfiles commands
configure: creating ./config.status
fast creating digikam/utilities/hotplug/digikam-download.desktop
fast creating digikam/utilities/hotplug/digikam-gphoto2-camera.desktop
config.pl: fast created 2 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
configure: creating ./config.status
fast creating digikam/utilities/hotplug/digikam-download.desktop
fast creating digikam/utilities/hotplug/digikam-gphoto2-camera.desktop
fast creating digikam/utilities/hotplug/digikam-mount-and-download.desktop
config.pl: fast created 3 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
checking if digikam should be compiled... yes
checking if doc should be compiled... yes
checking if po should be compiled... yes
configure: creating ./config.status
fast creating digikam/utilities/hotplug/digikam-download.desktop
fast creating digikam/utilities/hotplug/digikam-gphoto2-camera.desktop
fast creating digikam/utilities/hotplug/digikam-mount-and-download.desktop
fast creating Makefile
fast creating digikam/Makefile

[...]

fast creating po/uk/Makefile
fast creating po/vi/Makefile
fast creating po/zh_CN/Makefile
fast creating po/zh_TW/Makefile
config.pl: fast created 97 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

-- digiKam configure results -------------------
-- sqlite3 found.................. YES
-- gphoto2 found.................. YES
-- libkipi found.................. YES
-- libtiff found.................. YES
-- libpng found................... YES
-- lcms found..................... YES
-- Exiv2 library found............ YES
------------------------------------------------

Good - your configure finished. Start make now

[yaro][/tmp/digikam-0.9.0-beta3]$

```
please note 
```
checking exiv2/exif.hpp usability... no
checking exiv2/exif.hpp presence... yes
configure: WARNING: exiv2/exif.hpp: present but cannot be compiled
configure: WARNING: exiv2/exif.hpp:     check for missing prerequisite headers?
configure: WARNING: exiv2/exif.hpp: see the Autoconf documentation
configure: WARNING: exiv2/exif.hpp:     section "Present But Cannot Be Compiled"
configure: WARNING: exiv2/exif.hpp: proceeding with the preprocessor's result
configure: WARNING: exiv2/exif.hpp: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for exiv2/exif.hpp... yes

```
This might be a main problem but how to fix it ?

```

[yaro][/tmp/digikam-0.9.0-beta3]$ make

[...]

make[5]: Wej&#347;cie do katalogu `/tmp/digikam-0.9.0-beta3/digikam/libs/widgets/metadata'
/usr//bin/moc ./metadatalistview.h -o metadatalistview.moc
if /bin/sh ../../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../digikam/libs/dmetadata -I../../../../digikam/libs/dimg -I../../../../digikam/digikam -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_CLEAN_NAMESPACE -fexceptions -MT metadatalistview.lo -MD -MP -MF ".deps/metadatalistview.Tpo" -c -o metadatalistview.lo metadatalistview.cpp; \
        then mv -f ".deps/metadatalistview.Tpo" ".deps/metadatalistview.Plo"; else rm -f ".deps/metadatalistview.Tpo"; exit 1; fi
if /bin/sh ../../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../digikam/libs/dmetadata -I../../../../digikam/libs/dimg -I../../../../digikam/digikam -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_CLEAN_NAMESPACE -fexceptions -MT metadatalistviewitem.lo -MD -MP -MF ".deps/metadatalistviewitem.Tpo" -c -o metadatalistviewitem.lo metadatalistviewitem.cpp; \
        then mv -f ".deps/metadatalistviewitem.Tpo" ".deps/metadatalistviewitem.Plo"; else rm -f ".deps/metadatalistviewitem.Tpo"; exit 1; fi
/usr//bin/moc ./metadatawidget.h -o metadatawidget.moc
if /bin/sh ../../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../digikam/libs/dmetadata -I../../../../digikam/libs/dimg -I../../../../digikam/digikam -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_CLEAN_NAMESPACE -fexceptions -MT metadatawidget.lo -MD -MP -MF ".deps/metadatawidget.Tpo" -c -o metadatawidget.lo metadatawidget.cpp; \
        then mv -f ".deps/metadatawidget.Tpo" ".deps/metadatawidget.Plo"; else rm -f ".deps/metadatawidget.Tpo"; exit 1; fi
/usr//bin/moc ./iptcwidget.h -o iptcwidget.moc
if /bin/sh ../../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../digikam/libs/dmetadata -I../../../../digikam/libs/dimg -I../../../../digikam/digikam -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -DQT_CLEAN_NAMESPACE -fexceptions -MT iptcwidget.lo -MD -MP -MF ".deps/iptcwidget.Tpo" -c -o iptcwidget.lo iptcwidget.cpp; \
        then mv -f ".deps/iptcwidget.Tpo" ".deps/iptcwidget.Plo"; else rm -f ".deps/iptcwidget.Tpo"; exit 1; fi
iptcwidget.cpp: In member function 'virtual QString Digikam::IptcWidget::getTagTitle(const QString&)':
iptcwidget.cpp:184: error: 'dataSetTitle' is not a member of 'Exiv2::IptcDataSets'
make[5]: *** [iptcwidget.lo] B&#322;&#261;d 1
make[5]: Opuszczenie katalogu `/tmp/digikam-0.9.0-beta3/digikam/libs/widgets/metadata'
make[4]: *** [all-recursive] B&#322;&#261;d 1
make[4]: Opuszczenie katalogu `/tmp/digikam-0.9.0-beta3/digikam/libs/widgets'
make[3]: *** [all-recursive] B&#322;&#261;d 1
make[3]: Opuszczenie katalogu `/tmp/digikam-0.9.0-beta3/digikam/libs'
make[2]: *** [all-recursive] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/tmp/digikam-0.9.0-beta3/digikam'
make[1]: *** [all-recursive] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/tmp/digikam-0.9.0-beta3'
make: *** [all] B&#322;&#261;d 2
[yaro][/tmp/digikam-0.9.0-beta3]$                

```

my packages:
```
[yaro][/tmp/digikam-0.9.0-beta3]$ dpkg -l g++ gcc cpp libexif-dev libexiv2-dev
Wybór=U=Nieznany/I=Instalacja/R=Usuni&#281;cie/P=Wyczyszczenie/H=Zatrzymanie
| Stan=N=Brak/I=Zainst./C=Skonfig./U=Rozpakowany/F=Nieskonfig./H=Wpó&#322;-zainst.
|/ B&#322;&#281;dy?=(brak)/H=Wstrzym./R=Do przeinst./X=Obydwa (Stan,B&#322;&#281;dy:wielk.lit.=&#378;le)
||/ Nazwa                              Wersja                             Opis
+++-==================================-==================================-====================================================================================
ii  cpp                                4.0.3-1                            The GNU C preprocessor (cpp)
ii  g++                                4.0.3-1                            The GNU C++ compiler
ii  gcc                                4.0.3-1                            The GNU C compiler
ii  libexif-dev                        0.6.12-2                           library to parse EXIF files (development files)
ii  libexiv2-dev                       0.7-9.1ubuntu1                     EXIF/IPTC metadata manipulation library - development files
[yaro][/tmp/digikam-0.9.0-beta3]$

```

---

### Post by Sir_Yaro on 2006-10-21
i found the solution.
libexiv2-dev was to old. its need to be in 0.10-1ubuntu0~dapper1 version at least.

---

