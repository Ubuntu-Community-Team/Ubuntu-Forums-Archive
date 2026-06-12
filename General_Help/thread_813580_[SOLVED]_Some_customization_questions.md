---
title: "[SOLVED] Some customization questions"
date: 2008-05-30
forum: General Help
---

### Post by uberlube on 2008-05-30
Hi guys. I have 2 questions for u guys about some things that I want to do with my desktop so here they are.

1) I want to change the window decorations on all my windows to something that suits my color scheme better. I know what your going to say "Why don't you just enable the advanced effects and use a Beryl theme?" Well, the reason for this is that compiz just doesnt want to work properly on my laptop and I really don't want to spend hours fixing it. Anyway, I downloaded a KDE 3.2 +    Window Decoration and I tried installing it using the instructions in KDE-Look found here:
[http://www.kde-look.org/content/show.php/Crystal?content=13969](http://www.kde-look.org/content/show.php/Crystal?content=13969)

And this is the output:
```
manaburn@manaburn-laptop:~/Desktop/crystal-1.0.6$ ./configure
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
checking for gcc option to accept ISO C89... none needed
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
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking size of int... 4
checking size of short... 2
checking size of long... 4
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking size of size_t... 4
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
checking for X... libraries /usr/lib, headers .
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
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
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
checking for makekdewidgets... /usr/bin/makekdewidgets
checking for xmllint... /usr/bin/xmllint
checking if client should be compiled... yes
checking if pics should be compiled... yes
configure: creating ./config.status
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1365.
config.status: creating Makefile
config.status: creating client/Makefile
config.status: creating client/config/Makefile
config.status: creating pics/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now

manaburn@manaburn-laptop:~/Desktop/crystal-1.0.6$ make
make  all-recursive
make[1]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6'
Making all in pics
make[2]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT embedtool.o -MD -MP -MF ".deps/embedtool.Tpo" \
          -c -o embedtool.o `test -f 'embedtool.cpp' || echo './'`embedtool.cpp; \
        then mv -f ".deps/embedtool.Tpo" ".deps/embedtool.Po"; \
        else rm -f ".deps/embedtool.Tpo"; exit 1; \
        fi
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o embedtool -L/usr/share/qt3/lib     embedtool.o -lqt-mt  -lz -lpng -lz -lm -lXext -lX11  -lSM -lICE -lpthread
Generating Button Themes...
./embedtool ./vista/*.png ./aqua/*.png ./default/*.png ./handpainted/*.png ./knifty/*.png ./svg/*.png ./kubuntu-dapper/*.png ./kubuntu-edgy/*.png ./kubuntu-feisty/*.png > tiles.h
./vista/vista_above_hovered.png
./vista/vista_above.png
./vista/vista_above_pressed.png
./vista/vista_below_hovered.png
./vista/vista_below.png
./vista/vista_below_pressed.png
./vista/vista_close_hovered.png
./vista/vista_close.png
./vista/vista_close_pressed.png
./vista/vista_help_hovered.png
./vista/vista_help.png
./vista/vista_help_pressed.png
./vista/vista_max_hovered.png
./vista/vista_max.png
./vista/vista_max_pressed.png
./vista/vista_menu_hovered.png
./vista/vista_menu.png
./vista/vista_menu_pressed.png
./vista/vista_min_hovered.png
./vista/vista_min.png
./vista/vista_min_pressed.png
./vista/vista_restore_hovered.png
./vista/vista_restore.png
./vista/vista_restore_pressed.png
./vista/vista_shade_hovered.png
./vista/vista_shade.png
./vista/vista_shade_pressed.png
./vista/vista_sticky_hovered.png
./vista/vista_sticky.png
./vista/vista_sticky_pressed.png
./vista/vista_un_above_hovered.png
./vista/vista_un_above.png
./vista/vista_un_above_pressed.png
./vista/vista_un_below_hovered.png
./vista/vista_un_below.png
./vista/vista_un_below_pressed.png
./vista/vista_un_shade_hovered.png
./vista/vista_un_shade.png
./vista/vista_un_shade_pressed.png
./vista/vista_un_sticky_hovered.png
./vista/vista_un_sticky.png
./vista/vista_un_sticky_pressed.png
./aqua/aqua_above.png
./aqua/aqua_below.png
./aqua/aqua_close.png
./aqua/aqua_default.png
./aqua/aqua_help.png
./aqua/aqua_max.png
./aqua/aqua_min.png
./aqua/aqua_shade.png
./aqua/aqua_sticky.png
./aqua/aqua_un_sticky.png
./default/crystal_above.png
./default/crystal_below.png
./default/crystal_close.png
./default/crystal_help.png
./default/crystal_max.png
./default/crystal_menu.png
./default/crystal_min.png
./default/crystal_restore.png
./default/crystal_shade.png
./default/crystal_sticky.png
./default/crystal_unabove.png
./default/crystal_unbelow.png
./default/crystal_un_sticky.png
./handpainted/handpainted_above.png
./handpainted/handpainted_below.png
./handpainted/handpainted_close.png
./handpainted/handpainted_help.png
./handpainted/handpainted_max.png
./handpainted/handpainted_min.png
./handpainted/handpainted_restore.png
./handpainted/handpainted_shade.png
./handpainted/handpainted_sticky.png
./handpainted/handpainted_unabove.png
./handpainted/handpainted_unbelow.png
./handpainted/handpainted_un_shade.png
./handpainted/handpainted_un_sticky.png
./knifty/knifty_above.png
./knifty/knifty_below.png
./knifty/knifty_close.png
./knifty/knifty_help.png
./knifty/knifty_max.png
./knifty/knifty_min.png
./knifty/knifty_restore.png
./knifty/knifty_shade.png
./knifty/knifty_sticky.png
./knifty/knifty_unabove.png
./knifty/knifty_unbelow.png
./knifty/knifty_un_sticky.png
./svg/svg_above.png
./svg/svg_below.png
./svg/svg_close.png
./svg/svg_help.png
./svg/svg_max.png
./svg/svg_menu.png
./svg/svg_min.png
./svg/svg_restore.png
./svg/svg_shade.png
./svg/svg_sticky.png
./svg/svg_unshade.png
./svg/svg_unsticky.png
./kubuntu-dapper/dapper_above_hovered.png
./kubuntu-dapper/dapper_above.png
./kubuntu-dapper/dapper_above_pressed.png
./kubuntu-dapper/dapper_below_hovered.png
./kubuntu-dapper/dapper_below.png
./kubuntu-dapper/dapper_below_pressed.png
./kubuntu-dapper/dapper_close_hovered.png
./kubuntu-dapper/dapper_close.png
./kubuntu-dapper/dapper_close_pressed.png
./kubuntu-dapper/dapper_help_hovered.png
./kubuntu-dapper/dapper_help.png
./kubuntu-dapper/dapper_help_pressed.png
./kubuntu-dapper/dapper_max_hovered.png
./kubuntu-dapper/dapper_max.png
./kubuntu-dapper/dapper_max_pressed.png
./kubuntu-dapper/dapper_menu_hovered.png
./kubuntu-dapper/dapper_menu.png
./kubuntu-dapper/dapper_menu_pressed.png
./kubuntu-dapper/dapper_min_hovered.png
./kubuntu-dapper/dapper_min.png
./kubuntu-dapper/dapper_min_pressed.png
./kubuntu-dapper/dapper_restore_hovered.png
./kubuntu-dapper/dapper_restore.png
./kubuntu-dapper/dapper_restore_pressed.png
./kubuntu-dapper/dapper_shade_hovered.png
./kubuntu-dapper/dapper_shade.png
./kubuntu-dapper/dapper_shade_pressed.png
./kubuntu-dapper/dapper_sticky_hovered.png
./kubuntu-dapper/dapper_sticky.png
./kubuntu-dapper/dapper_sticky_pressed.png
./kubuntu-dapper/dapper_un_above_hovered.png
./kubuntu-dapper/dapper_un_above.png
./kubuntu-dapper/dapper_un_above_pressed.png
./kubuntu-dapper/dapper_un_below_hovered.png
./kubuntu-dapper/dapper_un_below.png
./kubuntu-dapper/dapper_un_below_pressed.png
./kubuntu-dapper/dapper_un_shade_hovered.png
./kubuntu-dapper/dapper_un_shade.png
./kubuntu-dapper/dapper_un_shade_pressed.png
./kubuntu-dapper/dapper_un_sticky_hovered.png
./kubuntu-dapper/dapper_un_sticky.png
./kubuntu-dapper/dapper_un_sticky_pressed.png
./kubuntu-edgy/edgy_above_hovered.png
./kubuntu-edgy/edgy_above.png
./kubuntu-edgy/edgy_above_pressed.png
./kubuntu-edgy/edgy_below_hovered.png
./kubuntu-edgy/edgy_below.png
./kubuntu-edgy/edgy_below_pressed.png
./kubuntu-edgy/edgy_close_hovered.png
./kubuntu-edgy/edgy_close.png
./kubuntu-edgy/edgy_close_pressed.png
./kubuntu-edgy/edgy_help_hovered.png
./kubuntu-edgy/edgy_help.png
./kubuntu-edgy/edgy_help_pressed.png
./kubuntu-edgy/edgy_max_hovered.png
./kubuntu-edgy/edgy_max.png
./kubuntu-edgy/edgy_max_pressed.png
./kubuntu-edgy/edgy_menu_hovered.png
./kubuntu-edgy/edgy_menu.png
./kubuntu-edgy/edgy_menu_pressed.png
./kubuntu-edgy/edgy_min_hovered.png
./kubuntu-edgy/edgy_min.png
./kubuntu-edgy/edgy_min_pressed.png
./kubuntu-edgy/edgy_restore_hovered.png
./kubuntu-edgy/edgy_restore.png
./kubuntu-edgy/edgy_restore_pressed.png
./kubuntu-edgy/edgy_shade_hovered.png
./kubuntu-edgy/edgy_shade.png
./kubuntu-edgy/edgy_shade_pressed.png
./kubuntu-edgy/edgy_sticky_hovered.png
./kubuntu-edgy/edgy_sticky.png
./kubuntu-edgy/edgy_sticky_pressed.png
./kubuntu-edgy/edgy_un_above_hovered.png
./kubuntu-edgy/edgy_un_above.png
./kubuntu-edgy/edgy_un_above_pressed.png
./kubuntu-edgy/edgy_un_below_hovered.png
./kubuntu-edgy/edgy_un_below.png
./kubuntu-edgy/edgy_un_below_pressed.png
./kubuntu-edgy/edgy_un_shade_hovered.png
./kubuntu-edgy/edgy_un_shade.png
./kubuntu-edgy/edgy_un_shade_pressed.png
./kubuntu-edgy/edgy_un_sticky_hovered.png
./kubuntu-edgy/edgy_un_sticky.png
./kubuntu-edgy/edgy_un_sticky_pressed.png
./kubuntu-feisty/feisty_above_hovered.png
./kubuntu-feisty/feisty_above.png
./kubuntu-feisty/feisty_above_pressed.png
./kubuntu-feisty/feisty_below_hovered.png
./kubuntu-feisty/feisty_below.png
./kubuntu-feisty/feisty_below_pressed.png
./kubuntu-feisty/feisty_close_hovered.png
./kubuntu-feisty/feisty_close.png
./kubuntu-feisty/feisty_close_pressed.png
./kubuntu-feisty/feisty_help_hovered.png
./kubuntu-feisty/feisty_help.png
./kubuntu-feisty/feisty_help_pressed.png
./kubuntu-feisty/feisty_max_hovered.png
./kubuntu-feisty/feisty_max.png
./kubuntu-feisty/feisty_max_pressed.png
./kubuntu-feisty/feisty_menu_hovered.png
./kubuntu-feisty/feisty_menu.png
./kubuntu-feisty/feisty_menu_pressed.png
./kubuntu-feisty/feisty_min_hovered.png
./kubuntu-feisty/feisty_min.png
./kubuntu-feisty/feisty_min_pressed.png
./kubuntu-feisty/feisty_restore_hovered.png
./kubuntu-feisty/feisty_restore.png
./kubuntu-feisty/feisty_restore_pressed.png
./kubuntu-feisty/feisty_shade_hovered.png
./kubuntu-feisty/feisty_shade.png
./kubuntu-feisty/feisty_shade_pressed.png
./kubuntu-feisty/feisty_sticky_hovered.png
./kubuntu-feisty/feisty_sticky.png
./kubuntu-feisty/feisty_sticky_pressed.png
./kubuntu-feisty/feisty_un_above_hovered.png
./kubuntu-feisty/feisty_un_above.png
./kubuntu-feisty/feisty_un_above_pressed.png
./kubuntu-feisty/feisty_un_below_hovered.png
./kubuntu-feisty/feisty_un_below.png
./kubuntu-feisty/feisty_un_below_pressed.png
./kubuntu-feisty/feisty_un_shade_hovered.png
./kubuntu-feisty/feisty_un_shade.png
./kubuntu-feisty/feisty_un_shade_pressed.png
./kubuntu-feisty/feisty_un_sticky_hovered.png
./kubuntu-feisty/feisty_un_sticky.png
./kubuntu-feisty/feisty_un_sticky_pressed.png
cp tiles.h ../client/tiles.h
Generating overlays...
./embedtool ./lighting_overlay.png ./glass_overlay.png ./steel_overlay.png > overlays.h
./lighting_overlay.png
./glass_overlay.png
./steel_overlay.png
cp overlays.h ../client/overlays.h
make[2]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
Making all in client
make[2]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client'
Making all in config
make[3]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
rm -rf configdialog.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./configdialog.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> configdialog.h ;
rm -rf infodialog.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./infodialog.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> infodialog.h ;
/usr/share/qt3/bin/moc ./crystalconfig.h -o crystalconfig.moc
if /bin/bash ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT crystalconfig.lo -MD -MP -MF ".deps/crystalconfig.Tpo" \
          -c -o crystalconfig.lo `test -f 'crystalconfig.cc' || echo './'`crystalconfig.cc; \
        then mv -f ".deps/crystalconfig.Tpo" ".deps/crystalconfig.Plo"; \
        else rm -f ".deps/crystalconfig.Tpo"; exit 1; \
        fi
/usr/share/qt3/bin/moc configdialog.h -o configdialog.moc
rm -f configdialog.cc
echo '#include <kdialog.h>' > configdialog.cc
echo '#include <klocale.h>' >> configdialog.cc
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -tr tr2i18n -i configdialog.h ./configdialog.ui > configdialog.cc.temp ; ret=$?; \
        /usr/bin/perl -pe "s,tr2i18n( \"\" ),QString::null,g" configdialog.cc.temp | /usr/bin/perl -pe "s,tr2i18n( \"\"\, \"\" ),QString::null,g" | /usr/bin/perl -pe "s,image([0-9][0-9]*)_data,img\$1_configdialog,g" | /usr/bin/perl -pe "s,: QWizard\(,: KWizard(,g" >> configdialog.cc ;\
        rm -f configdialog.cc.temp ;\
        if test "$ret" = 0; then echo '#include "configdialog.moc"' >> configdialog.cc; else rm -f configdialog.cc ; exit $ret ; fi
if /bin/bash ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT configdialog.lo -MD -MP -MF ".deps/configdialog.Tpo" \
          -c -o configdialog.lo `test -f 'configdialog.cc' || echo './'`configdialog.cc; \
        then mv -f ".deps/configdialog.Tpo" ".deps/configdialog.Plo"; \
        else rm -f ".deps/configdialog.Tpo"; exit 1; \
        fi
/usr/share/qt3/bin/moc infodialog.h -o infodialog.moc
rm -f infodialog.cc
echo '#include <kdialog.h>' > infodialog.cc
echo '#include <klocale.h>' >> infodialog.cc
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -tr tr2i18n -i infodialog.h ./infodialog.ui > infodialog.cc.temp ; ret=$?; \
        /usr/bin/perl -pe "s,tr2i18n( \"\" ),QString::null,g" infodialog.cc.temp | /usr/bin/perl -pe "s,tr2i18n( \"\"\, \"\" ),QString::null,g" | /usr/bin/perl -pe "s,image([0-9][0-9]*)_data,img\$1_infodialog,g" | /usr/bin/perl -pe "s,: QWizard\(,: KWizard(,g" >> infodialog.cc ;\
        rm -f infodialog.cc.temp ;\
        if test "$ret" = 0; then echo '#include "infodialog.moc"' >> infodialog.cc; else rm -f infodialog.cc ; exit $ret ; fi
if /bin/bash ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT infodialog.lo -MD -MP -MF ".deps/infodialog.Tpo" \
          -c -o infodialog.lo `test -f 'infodialog.cc' || echo './'`infodialog.cc; \
        then mv -f ".deps/infodialog.Tpo" ".deps/infodialog.Plo"; \
        else rm -f ".deps/infodialog.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN   -o kwin_crystal_config.la -rpath /usr/lib/kde3 -module -L/usr/share/qt3/lib     -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -R /usr/lib -R /usr/lib -R /usr/share/qt3/lib  crystalconfig.lo configdialog.lo infodialog.lo -lkdeui -lkio -lqt-mt  -lz -lpng -lz -lm -lXext -lX11  -lSM -lICE -lpthread -lkdecore
make[3]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
make[3]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client'
/usr/share/qt3/bin/moc ./crystalclient.h -o crystalclient.moc
if /bin/bash ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/kde/kwin  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -MT crystalclient.lo -MD -MP -MF ".deps/crystalclient.Tpo" \
          -c -o crystalclient.lo `test -f 'crystalclient.cc' || echo './'`crystalclient.cc; \
        then mv -f ".deps/crystalclient.Tpo" ".deps/crystalclient.Plo"; \
        else rm -f ".deps/crystalclient.Tpo"; exit 1; \
        fi
In file included from crystalclient.cc:38:
crystalclient.h:31:25: error: kdecoration.h: No such file or directory
crystalclient.h:32:32: error: kdecorationfactory.h: No such file or directory
crystalclient.cc:136:5: warning: "KDE_IS_VERSION" is not defined
crystalclient.cc:136:19: error: missing binary operator before token "("
crystalclient.cc:1153:5: warning: "KDE_IS_VERSION" is not defined
crystalclient.cc:1153:19: error: missing binary operator before token "("
crystalclient.cc:1164:5: warning: "KDE_IS_VERSION" is not defined
crystalclient.cc:1164:19: error: missing binary operator before token "("
crystalclient.h:102: error: expected class-name before '{' token
crystalclient.h:106: error: ISO C++ forbids declaration of 'KDecoration' with no type
crystalclient.h:106: error: 'KDecoration' declared as a 'virtual' field
crystalclient.h:106: error: expected ';' before '*' token
crystalclient.h:108: error: 'Ability' has not been declared
crystalclient.h:146: error: expected class-name before '{' token
crystalclient.h:149: error: expected `)' before '*' token
crystalclient.h:164: error: 'Position' does not name a type
crystalclient.cc:54: error: expected constructor, destructor, or type conversion before '*' token
crystalclient.cc: In member function 'virtual void CCrystalTooltip::maybeTip(const QPoint&)':
crystalclient.cc:73: error: 'class CrystalClient' has no member named 'caption'
crystalclient.cc: At global scope:
crystalclient.cc:107: error: expected constructor, destructor, or type conversion before '*' token
crystalclient.cc:132: error: 'bool CrystalFactory::supports' is not a static member of 'class CrystalFactory'
crystalclient.cc:132: error: 'Ability' was not declared in this scope
crystalclient.cc:133: error: expected ',' or ';' before '{' token
crystalclient.cc:673: error: expected `)' before '*' token
crystalclient.cc: In member function 'virtual void CrystalClient::init()':
crystalclient.cc:689: error: 'WResizeNoErase' was not declared in this scope
crystalclient.cc:689: error: 'WRepaintNoErase' was not declared in this scope
crystalclient.cc:689: error: 'createMainWidget' was not declared in this scope
crystalclient.cc:690: error: 'widget' was not declared in this scope
crystalclient.cc:693: error: 'options' was not declared in this scope
crystalclient.cc:694: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:694: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:697: error: 'NoBackground' was not declared in this scope
crystalclient.cc:713: error: 'isPreview' was not declared in this scope
crystalclient.cc:729: error: 'options' was not declared in this scope
crystalclient.cc:738: error: 'connect' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::updateMask()':
crystalclient.cc:749: error: 'options' was not declared in this scope
crystalclient.cc:749: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:749: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:751: error: 'widget' was not declared in this scope
crystalclient.cc:751: error: 'setMask' was not declared in this scope
crystalclient.cc:756: error: 'width' was not declared in this scope
crystalclient.cc:757: error: 'height' was not declared in this scope
crystalclient.cc:760: error: 'widget' was not declared in this scope
crystalclient.cc:791: error: 'setMask' was not declared in this scope
crystalclient.cc: In member function 'CrystalButton* CrystalClient::addButtons(QBoxLayout*, const QString&)':
crystalclient.cc:809: error: 'connect' was not declared in this scope
crystalclient.cc:815: error: 'isOnAllDesktops' was not declared in this scope
crystalclient.cc:823: error: 'connect' was not declared in this scope
crystalclient.cc:828: error: 'providesContextHelp' was not declared in this scope
crystalclient.cc:831: error: 'connect' was not declared in this scope
crystalclient.cc:836: error: 'isMinimizable' was not declared in this scope
crystalclient.cc:839: error: 'connect' was not declared in this scope
crystalclient.cc:846: error: 'keepAbove' was not declared in this scope
crystalclient.cc:847: error: 'connect' was not declared in this scope
crystalclient.cc:854: error: 'keepBelow' was not declared in this scope
crystalclient.cc:855: error: 'connect' was not declared in this scope
crystalclient.cc:860: error: 'isShadeable' was not declared in this scope
crystalclient.cc:863: error: 'connect' was not declared in this scope
crystalclient.cc:868: error: 'isMaximizable' was not declared in this scope
crystalclient.cc:870: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:870: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:880: error: 'connect' was not declared in this scope
crystalclient.cc:885: error: 'isCloseable' was not declared in this scope
crystalclient.cc:888: error: 'connect' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::activeChange()':
crystalclient.cc:912: error: 'isActive' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::captionChange()':
crystalclient.cc:917: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::desktopChange()':
crystalclient.cc:922: error: 'isOnAllDesktops' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::maximizeChange()':
crystalclient.cc:939: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:939: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:946: error: 'options' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::updateLayout()':
crystalclient.cc:968: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::shadeChange()':
crystalclient.cc:982: error: 'isShade' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::borders(int&, int&, int&, int&) const':
crystalclient.cc:992: error: 'isShade' was not declared in this scope
crystalclient.cc:994: error: 'options' was not declared in this scope
crystalclient.cc:1002: error: 'isShade' was not declared in this scope
crystalclient.cc:1003: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:1003: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc: In member function 'virtual void CrystalClient::resize(const QSize&)':
crystalclient.cc:1010: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'virtual QSize CrystalClient::minimumSize() const':
crystalclient.cc:1015: error: 'widget' was not declared in this scope
crystalclient.cc: At global scope:
crystalclient.cc:1018: error: 'KDecoration' has not been declared
crystalclient.cc:1018: error: expected constructor, destructor, or type conversion before 'CrystalClient'
crystalclient.cc: In member function 'bool CrystalClient::eventFilter(QObject*, QEvent*)':
crystalclient.cc:1054: error: 'widget' was not declared in this scope
crystalclient.cc:1061: error: 'processMousePressEvent' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::ClientWindows(Window*, Window*, Window*)':
crystalclient.cc:1094: error: 'widget' was not declared in this scope
crystalclient.cc:1105: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::mouseDoubleClickEvent(QMouseEvent*)':
crystalclient.cc:1123: error: 'LeftButton' was not declared in this scope
crystalclient.cc:1123: error: 'titlebarDblClickOperation' was not declared in this scope
crystalclient.cc:1126: error: 'processMousePressEvent' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::mouseWheelEvent(QWheelEvent*)':
crystalclient.cc:1136: error: 'class CrystalClient' has no member named 'isActive'
crystalclient.cc:1159: error: 'class CrystalClient' has no member named 'desktop'
crystalclient.cc:1159: error: 'desktop' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::paintEvent(QPaintEvent*)':
crystalclient.cc:1175: error: 'widget' was not declared in this scope
crystalclient.cc:1178: error: 'options' was not declared in this scope
crystalclient.cc:1178: error: 'KDecoration' has not been declared
crystalclient.cc:1178: error: 'isActive' was not declared in this scope
crystalclient.cc:1212: error: 'KDecoration' has not been declared
crystalclient.cc:1222: error: 'caption' was not declared in this scope
crystalclient.cc:1225: error: 'AlignLeft' was not declared in this scope
crystalclient.cc:1230: error: 'AlignVCenter' was not declared in this scope
crystalclient.cc:1236: error: 'AlignVCenter' was not declared in this scope
crystalclient.cc:1242: error: 'AlignLeft' was not declared in this scope
crystalclient.cc:1243: error: 'AlignLeft' was not declared in this scope
crystalclient.cc:1245: error: 'AlignRight' was not declared in this scope
crystalclient.cc:1246: error: 'AlignRight' was not declared in this scope
crystalclient.cc:1248: error: 'AlignHCenter' was not declared in this scope
crystalclient.cc:1249: error: 'AlignHCenter' was not declared in this scope
crystalclient.cc:1265: error: 'isShade' was not declared in this scope
crystalclient.cc:1265: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:1265: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:1295: error: 'isShade' was not declared in this scope
crystalclient.cc:1344: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:1344: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:1347: error: 'width' was not declared in this scope
crystalclient.cc:1348: error: 'height' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::resizeEvent(QResizeEvent*)':
crystalclient.cc:1395: error: 'widget' was not declared in this scope
crystalclient.cc:1407: error: 'isActive' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::moveEvent(QMoveEvent*)':
crystalclient.cc:1420: error: 'widget' was not declared in this scope
crystalclient.cc:1431: error: 'isActive' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::showEvent(QShowEvent*)':
crystalclient.cc:1440: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::Repaint()':
crystalclient.cc:1446: error: 'widget' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::maxButtonPressed()':
crystalclient.cc:1457: error: 'MidButton' was not declared in this scope
crystalclient.cc:1458: error: 'maximizeMode' was not declared in this scope
crystalclient.cc:1458: error: 'MaximizeVertical' was not declared in this scope
crystalclient.cc:1458: error: 'maximize' was not declared in this scope
crystalclient.cc:1460: error: 'RightButton' was not declared in this scope
crystalclient.cc:1461: error: 'MaximizeHorizontal' was not declared in this scope
crystalclient.cc:1464: error: 'MaximizeFull' was not declared in this scope
crystalclient.cc:1464: error: 'MaximizeRestore' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::minButtonPressed()':
crystalclient.cc:1473: error: 'MidButton' was not declared in this scope
crystalclient.cc:1474: error: 'LowerOp' was not declared in this scope
crystalclient.cc:1474: error: 'performWindowOperation' was not declared in this scope
crystalclient.cc:1477: error: 'RightButton' was not declared in this scope
crystalclient.cc:1478: error: 'isShadeable' was not declared in this scope
crystalclient.cc:1478: error: 'isShade' was not declared in this scope
crystalclient.cc:1478: error: 'setShade' was not declared in this scope
crystalclient.cc:1481: error: 'minimize' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::aboveButtonPressed()':
crystalclient.cc:1488: error: 'keepAbove' was not declared in this scope
crystalclient.cc:1488: error: 'setKeepAbove' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::belowButtonPressed()':
crystalclient.cc:1493: error: 'keepBelow' was not declared in this scope
crystalclient.cc:1493: error: 'setKeepBelow' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::keepAboveChange(bool)':
crystalclient.cc:1500: error: 'keepAbove' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::keepBelowChange(bool)':
crystalclient.cc:1508: error: 'keepBelow' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::closeButtonPressed()':
crystalclient.cc:1516: error: 'RightButton' was not declared in this scope
crystalclient.cc:1532: error: 'closeWindow' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::shadeButtonPressed()':
crystalclient.cc:1541: error: 'MidButton' was not declared in this scope
crystalclient.cc:1542: error: 'RightButton' was not declared in this scope
crystalclient.cc:1545: error: 'isShadeable' was not declared in this scope
crystalclient.cc:1545: error: 'isShade' was not declared in this scope
crystalclient.cc:1545: error: 'setShade' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::menuButtonPressed()':
crystalclient.cc:1564: error: 'closeWindow' was not declared in this scope
crystalclient.cc: In member function 'void CrystalClient::menuPopUp()':
crystalclient.cc:1575: error: 'KDecorationFactory' was not declared in this scope
crystalclient.cc:1575: error: 'f' was not declared in this scope
crystalclient.cc:1575: error: 'factory' cannot be used as a function
crystalclient.cc:1576: error: 'showWindowMenu' was not declared in this scope
crystalclient.moc: In static member function 'static QMetaObject* CrystalClient::staticMetaObject()':
crystalclient.moc:54: error: 'KDecoration' has not been declared
crystalclient.moc: In member function 'virtual void* CrystalClient::qt_cast(const char*)':
crystalclient.moc:102: error: 'KDecoration' has not been declared
crystalclient.moc: In member function 'virtual bool CrystalClient::qt_invoke(int, QUObject*)':
crystalclient.moc:120: error: 'KDecoration' has not been declared
crystalclient.moc: In member function 'virtual bool CrystalClient::qt_emit(int, QUObject*)':
crystalclient.moc:127: error: 'KDecoration' has not been declared
crystalclient.moc: In member function 'virtual bool CrystalClient::qt_property(int, int, QVariant*)':
crystalclient.moc:133: error: 'KDecoration' has not been declared
make[3]: *** [crystalclient.lo] Error 1
make[3]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6'
make: *** [all] Error 2
manaburn@manaburn-laptop:~/Desktop/crystal-1.0.6$ make install
Making install in pics
make[1]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
make[2]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
make[1]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/pics'
Making install in client
make[1]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client'
Making install in config
make[2]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
make[3]: Entering directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
/bin/bash ../../admin/mkinstalldirs /usr/lib/kde3
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c -p  kwin_crystal_config.la /usr/lib/kde3/kwin_crystal_config.la
/usr/bin/install: cannot remove `/usr/lib/kde3/kwin_crystal_config.so': Permission denied
make[3]: *** [install-kde_moduleLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client/config'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/manaburn/Desktop/crystal-1.0.6/client'
make: *** [install-recursive] Error 1
manaburn@manaburn-laptop:~/Desktop/crystal-1.0.6$                             
```

Am I missing something here or is there an easier way to go about installing these.

2) My second question is how can I activate the feature where the window slides up into the title bar? (I believe its called 'Shader' but I could be mistaken) I know that it can be done without the help of compiz because you can do it in the XFCE environment, but is it usable in KDE the same way?

As always, thats for the help :)

---

### Post by Genius314 on 2008-05-30
1. It's in the repositories:

```
sudo apt-get install kwin-style-crystal
```

---

### Post by uberlube on 2008-05-30
k thnx. ill give it a try to see if its the same one.

---

### Post by uberlube on 2008-05-30
K that should be good for now, thanks for the help. Can u answer my second question while your still here?

---

### Post by Genius314 on 2008-05-31
Well, I don't use KDE, so I wouldn't know how to do it (I don't even know how to get shade to work in Gnome, only in Compiz).
Sorry. :(

---

### Post by uberlube on 2008-05-31
No prob thanks for the help anyways :)

---

### Post by Forlong on 2008-05-31
Add this to your **~/.kde/share/config/kwinrc** (that is a file in a hidden folder of your home directory) under **[Windows]**
```
TitlebarDoubleClickCommand=Shade
```

---

### Post by uberlube on 2008-06-01
I knew it was possible, thanks! U da man! :)

---

