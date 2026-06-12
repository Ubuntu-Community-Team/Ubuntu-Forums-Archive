---
title: "splashy compile errors"
date: 2006-10-29
forum: General Help
---

### Post by compwiz18 on 2006-10-29
I'm trying to compile splashy 2.1 on my AMD64 kernel machine.  It isn't working, and I suspect I am missing dependencies somewhere...

Help is appreciated.

Errors follow:

```
make  all-recursive
make[1]: Entering directory `/home/adam/splashy/splashy-0.2.1'
Making all in doc
make[2]: Entering directory `/home/adam/splashy/splashy-0.2.1/doc'
pod2man --release 1.0 --section 1 --center "Splashy POSIX boot splash system" --date `date +%Y-%m-%d` --name "SPLASHY" splashy.pod > splashy.1
pod2man --release 1.0 --section 1 --center "Splashy POSIX boot splash system" --date `date +%Y-%m-%d` --name "SPLASHY_CONFIG" splashy_config.pod > splashy_config.1
pod2man --release 1.0 --section 1 --center "Splashy POSIX boot splash system" --date `date +%Y-%m-%d` --name "SPLASHY_UPDATE" splashy_update.pod > splashy_update.1
pod2man --release 1.0 --section 1 --center "Splashy POSIX boot splash system" --date `date +%Y-%m-%d` --name "SPLASHY_UPDATE" splashy-config_xml.pod > splashy-config_xml.5
pod2man --release 1.0 --section 1 --center "Splashy POSIX boot splash system" --date `date +%Y-%m-%d` --name "SPLASHY_UPDATE" splashy-theme_xml.pod > splashy-theme_xml.5
make[2]: Leaving directory `/home/adam/splashy/splashy-0.2.1/doc'
Making all in src
make[2]: Entering directory `/home/adam/splashy/splashy-0.2.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-splashy_main.o -MD -MP -MF ".deps/splashy-splashy_main.Tpo" -c -o splashy-splashy_main.o `test -f 'splashy_main.c' || echo './'`splashy_main.c; \
        then mv -f ".deps/splashy-splashy_main.Tpo" ".deps/splashy-splashy_main.Po"; else rm -f ".deps/splashy-splashy_main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-splashy_functions.o -MD -MP -MF ".deps/splashy-splashy_functions.Tpo" -c -o splashy-splashy_functions.o `test -f 'splashy_functions.c' || echo './'`splashy_functions.c; \
        then mv -f ".deps/splashy-splashy_functions.Tpo" ".deps/splashy-splashy_functions.Po"; else rm -f ".deps/splashy-splashy_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-xml_parser.o -MD -MP -MF ".deps/splashy-xml_parser.Tpo" -c -o splashy-xml_parser.o `test -f 'xml_parser.c' || echo './'`xml_parser.c; \
        then mv -f ".deps/splashy-xml_parser.Tpo" ".deps/splashy-xml_parser.Po"; else rm -f ".deps/splashy-xml_parser.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-xml_config.o -MD -MP -MF ".deps/splashy-xml_config.Tpo" -c -o splashy-xml_config.o `test -f 'xml_config.c' || echo './'`xml_config.c; \
        then mv -f ".deps/splashy-xml_config.Tpo" ".deps/splashy-xml_config.Po"; else rm -f ".deps/splashy-xml_config.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-splashy_video.o -MD -MP -MF ".deps/splashy-splashy_video.Tpo" -c -o splashy-splashy_video.o `test -f 'splashy_video.c' || echo './'`splashy_video.c; \
        then mv -f ".deps/splashy-splashy_video.Tpo" ".deps/splashy-splashy_video.Po"; else rm -f ".deps/splashy-splashy_video.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy-common_functions.o -MD -MP -MF ".deps/splashy-common_functions.Tpo" -c -o splashy-common_functions.o `test -f 'common_functions.c' || echo './'`common_functions.c; \
        then mv -f ".deps/splashy-common_functions.Tpo" ".deps/splashy-common_functions.Po"; else rm -f ".deps/splashy-common_functions.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS   -o splashy -static -all_load -lgcc_s -lpthread -lm -lc -static /usr/lib/directfb-0.9.24/systems/libdirectfb_fbdev.a /usr/lib/libsysfs.a /usr/lib/directfb-0.9.24/wm/libdirectfbwm_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_ft2.a /usr/lib/libfreetype.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_gif.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_png.a /usr/lib/libpng.a /usr/lib/libz.a /usr/lib/libm.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_jpeg.a /usr/lib/libjpeg.a /usr/lib/directfb-0.9.24/inputdrivers/libdirectfb_keyboard.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_ati128.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_cyber5k.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i810.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i830.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_mach64.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_matrox.a /usr/lib/libsysfs.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_neomagic.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nsc.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nvidia.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_r200.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_radeon.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_savage.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_sis315.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_tdfx.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_unichrome.a -L/usr/lib /usr/lib/libdirectfb.a /usr/lib/libfusion.a /usr/lib/libdirect.a /usr/lib/libpthread.a /usr/lib/libz.a /usr/lib/libglib-2.0.a -static /usr/lib/directfb-0.9.24/systems/libdirectfb_fbdev.a /usr/lib/libsysfs.a /usr/lib/directfb-0.9.24/wm/libdirectfbwm_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_ft2.a /usr/lib/libfreetype.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_gif.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_png.a /usr/lib/libpng.a /usr/lib/libz.a /usr/lib/libm.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_jpeg.a /usr/lib/libjpeg.a /usr/lib/directfb-0.9.24/inputdrivers/libdirectfb_keyboard.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_ati128.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_cyber5k.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i810.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i830.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_mach64.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_matrox.a /usr/lib/libsysfs.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_neomagic.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nsc.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nvidia.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_r200.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_radeon.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_savage.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_sis315.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_tdfx.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_unichrome.a -L/usr/lib /usr/lib/libdirectfb.a /usr/lib/libfusion.a /usr/lib/libdirect.a /usr/lib/libpthread.a /usr/lib/libz.a  -Wl,-udirectfb_fbdev -Wl,-udirectfbwm_default -Wl,-uIDirectFBFont_Default -Wl,-uIDirectFBFont_FT2 -Wl,-uIDirectFBImageProvider_GIF -Wl,-uIDirectFBImageProvider_PNG -Wl,-uIDirectFBImageProvider_JPEG -Wl,-udirectfb_keyboard -Wl,-udirectfb_ati128 -Wl,-udirectfb_cyber5k -Wl,-udirectfb_i810 -Wl,-udirectfb_i830 -Wl,-udirectfb_mach64 -Wl,-udirectfb_neomagic -Wl,-udirectfb_nsc -Wl,-udirectfb_radeon -Wl,-udirectfb_savage -Wl,-udirectfb_sis315 -Wl,-udirectfb_tdfx splashy-splashy_main.o splashy-splashy_functions.o splashy-xml_parser.o splashy-xml_config.o splashy-splashy_video.o splashy-common_functions.o  
mkdir .libs
gcc -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -o splashy -all_load -Wl,-udirectfb_fbdev -Wl,-udirectfbwm_default -Wl,-uIDirectFBFont_Default -Wl,-uIDirectFBFont_FT2 -Wl,-uIDirectFBImageProvider_GIF -Wl,-uIDirectFBImageProvider_PNG -Wl,-uIDirectFBImageProvider_JPEG -Wl,-udirectfb_keyboard -Wl,-udirectfb_ati128 -Wl,-udirectfb_cyber5k -Wl,-udirectfb_i810 -Wl,-udirectfb_i830 -Wl,-udirectfb_mach64 -Wl,-udirectfb_neomagic -Wl,-udirectfb_nsc -Wl,-udirectfb_radeon -Wl,-udirectfb_savage -Wl,-udirectfb_sis315 -Wl,-udirectfb_tdfx splashy-splashy_main.o splashy-splashy_functions.o splashy-xml_parser.o splashy-xml_config.o splashy-splashy_video.o splashy-common_functions.o  -lgcc_s -lpthread -lm -lc -L/usr/lib /usr/lib/libglib-2.0.a /usr/lib/directfb-0.9.24/systems/libdirectfb_fbdev.a /usr/lib/directfb-0.9.24/wm/libdirectfbwm_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_default.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBFont/libidirectfbfont_ft2.a /usr/lib/libfreetype.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_gif.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_png.a /usr/lib/libpng.a /usr/lib/libm.a /usr/lib/directfb-0.9.24/interfaces/IDirectFBImageProvider/libidirectfbimageprovider_jpeg.a /usr/lib/libjpeg.a /usr/lib/directfb-0.9.24/inputdrivers/libdirectfb_keyboard.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_ati128.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_cyber5k.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i810.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_i830.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_mach64.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_matrox.a /usr/lib/libsysfs.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_neomagic.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nsc.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_nvidia.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_r200.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_radeon.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_savage.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_sis315.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_tdfx.a /usr/lib/directfb-0.9.24/gfxdrivers/libdirectfb_unichrome.a /usr/lib/libdirectfb.a /usr/lib/libfusion.a /usr/lib/libdirect.a /usr/lib/libpthread.a /usr/lib/libz.a
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-splashy_config-main.o -MD -MP -MF ".deps/splashy_config-splashy_config-main.Tpo" -c -o splashy_config-splashy_config-main.o `test -f 'splashy_config-main.c' || echo './'`splashy_config-main.c; \
        then mv -f ".deps/splashy_config-splashy_config-main.Tpo" ".deps/splashy_config-splashy_config-main.Po"; else rm -f ".deps/splashy_config-splashy_config-main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-splashy_config-functions.o -MD -MP -MF ".deps/splashy_config-splashy_config-functions.Tpo" -c -o splashy_config-splashy_config-functions.o `test -f 'splashy_config-functions.c' || echo './'`splashy_config-functions.c; \
        then mv -f ".deps/splashy_config-splashy_config-functions.Tpo" ".deps/splashy_config-splashy_config-functions.Po"; else rm -f ".deps/splashy_config-splashy_config-functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_functions.o -MD -MP -MF ".deps/splashy_config-xml_functions.Tpo" -c -o splashy_config-xml_functions.o `test -f 'xml_functions.c' || echo './'`xml_functions.c; \
        then mv -f ".deps/splashy_config-xml_functions.Tpo" ".deps/splashy_config-xml_functions.Po"; else rm -f ".deps/splashy_config-xml_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_config.o -MD -MP -MF ".deps/splashy_config-xml_config.Tpo" -c -o splashy_config-xml_config.o `test -f 'xml_config.c' || echo './'`xml_config.c; \
        then mv -f ".deps/splashy_config-xml_config.Tpo" ".deps/splashy_config-xml_config.Po"; else rm -f ".deps/splashy_config-xml_config.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-common_functions.o -MD -MP -MF ".deps/splashy_config-common_functions.Tpo" -c -o splashy_config-common_functions.o `test -f 'common_functions.c' || echo './'`common_functions.c; \
        then mv -f ".deps/splashy_config-common_functions.Tpo" ".deps/splashy_config-common_functions.Po"; else rm -f ".deps/splashy_config-common_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_parser.o -MD -MP -MF ".deps/splashy_config-xml_parser.Tpo" -c -o splashy_config-xml_parser.o `test -f 'xml_parser.c' || echo './'`xml_parser.c; \
        then mv -f ".deps/splashy_config-xml_parser.Tpo" ".deps/splashy_config-xml_parser.Po"; else rm -f ".deps/splashy_config-xml_parser.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS   -o splashy_config -static -all_load  /usr/lib/libglib-2.0.a /usr/lib/libmagic.a /usr/lib/libz.a splashy_config-splashy_config-main.o splashy_config-splashy_config-functions.o splashy_config-xml_functions.o splashy_config-xml_config.o splashy_config-common_functions.o splashy_config-xml_parser.o  
gcc -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -o splashy_config -all_load splashy_config-splashy_config-main.o splashy_config-splashy_config-functions.o splashy_config-xml_functions.o splashy_config-xml_config.o splashy_config-common_functions.o splashy_config-xml_parser.o  /usr/lib/libglib-2.0.a /usr/lib/libmagic.a /usr/lib/libz.a
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-splashy_update.o -MD -MP -MF ".deps/splashy_update-splashy_update.Tpo" -c -o splashy_update-splashy_update.o `test -f 'splashy_update.c' || echo './'`splashy_update.c; \
        then mv -f ".deps/splashy_update-splashy_update.Tpo" ".deps/splashy_update-splashy_update.Po"; else rm -f ".deps/splashy_update-splashy_update.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-xml_config.o -MD -MP -MF ".deps/splashy_update-xml_config.Tpo" -c -o splashy_update-xml_config.o `test -f 'xml_config.c' || echo './'`xml_config.c; \
        then mv -f ".deps/splashy_update-xml_config.Tpo" ".deps/splashy_update-xml_config.Po"; else rm -f ".deps/splashy_update-xml_config.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-common_functions.o -MD -MP -MF ".deps/splashy_update-common_functions.Tpo" -c -o splashy_update-common_functions.o `test -f 'common_functions.c' || echo './'`common_functions.c; \
        then mv -f ".deps/splashy_update-common_functions.Tpo" ".deps/splashy_update-common_functions.Po"; else rm -f ".deps/splashy_update-common_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-xml_parser.o -MD -MP -MF ".deps/splashy_update-xml_parser.Tpo" -c -o splashy_update-xml_parser.o `test -f 'xml_parser.c' || echo './'`xml_parser.c; \
        then mv -f ".deps/splashy_update-xml_parser.Tpo" ".deps/splashy_update-xml_parser.Po"; else rm -f ".deps/splashy_update-xml_parser.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS   -o splashy_update  /usr/lib/libglib-2.0.a splashy_update-splashy_update.o splashy_update-xml_config.o splashy_update-common_functions.o splashy_update-xml_parser.o  
gcc -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -o splashy_update splashy_update-splashy_update.o splashy_update-xml_config.o splashy_update-common_functions.o splashy_update-xml_parser.o  /usr/lib/libglib-2.0.a
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_pgrep-splashy_pgrep.o -MD -MP -MF ".deps/splashy_pgrep-splashy_pgrep.Tpo" -c -o splashy_pgrep-splashy_pgrep.o `test -f 'splashy_pgrep.c' || echo './'`splashy_pgrep.c; \
        then mv -f ".deps/splashy_pgrep-splashy_pgrep.Tpo" ".deps/splashy_pgrep-splashy_pgrep.Po"; else rm -f ".deps/splashy_pgrep-splashy_pgrep.Tpo"; exit 1; fi
splashy_pgrep.c:30:27: error: proc/readproc.h: No such file or directory
splashy_pgrep.c:31:22: error: proc/sig.h: No such file or directory
splashy_pgrep.c:32:26: error: proc/devname.h: No such file or directory
splashy_pgrep.c:33:26: error: proc/sysinfo.h: No such file or directory
splashy_pgrep.c:34:47: error: proc/version.h: No such file or directory
splashy_pgrep.c: In function ‘usage’:
splashy_pgrep.c:65: error: expected declaration specifiers before ‘NORETURN’
splashy_pgrep.c:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
splashy_pgrep.c:80: error: expected ‘;’, ‘,’ or ‘)’ before ‘str’
splashy_pgrep.c:124: error: expected ‘;’, ‘,’ or ‘)’ before ‘str’
splashy_pgrep.c:147: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:166: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:185: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:199: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:213: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:225: error: expected ‘;’, ‘,’ or ‘)’ before ‘name’
splashy_pgrep.c:233: error: expected ‘;’, ‘,’ or ‘)’ before ‘list’
splashy_pgrep.c:249: error: expected ‘;’, ‘,’ or ‘)’ before ‘value’
splashy_pgrep.c:265: error: expected ‘;’, ‘,’ or ‘)’ before ‘list’
splashy_pgrep.c:276: error: expected ‘;’, ‘,’ or ‘)’ before ‘list’
splashy_pgrep.c:287: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
splashy_pgrep.c:320: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
splashy_pgrep.c:352: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
splashy_pgrep.c:479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
splashy_pgrep.c:610: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
splashy_pgrep.c:631: error: expected ‘{’ at end of input
make[2]: *** [splashy_pgrep-splashy_pgrep.o] Error 1
make[2]: Leaving directory `/home/adam/splashy/splashy-0.2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/splashy/splashy-0.2.1'
make: *** [all] Error 2

```

---

### Post by UnknowUser on 2006-12-16
I've the same problem when try to make:

```
make  all-recursive
make[1]: Entering directory `/home/user/Downloads/splashy-0.2.1'
Making all in doc
make[2]: Entering directory `/home/user/Downloads/splashy-0.2.1/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/user/Downloads/splashy-0.2.1/doc'
Making all in src
make[2]: Entering directory `/home/user/Downloads/splashy-0.2.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-splashy_config-functions.o -MD -MP -MF ".deps/splashy_config-splashy_config-functions.Tpo" -c -o splashy_config-splashy_config-functions.o `test -f 'splashy_config-functions.c' || echo './'`splashy_config-functions.c; \
        then mv -f ".deps/splashy_config-splashy_config-functions.Tpo" ".deps/splashy_config-splashy_config-functions.Po"; else rm -f ".deps/splashy_config-splashy_config-functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_functions.o -MD -MP -MF ".deps/splashy_config-xml_functions.Tpo" -c -o splashy_config-xml_functions.o `test -f 'xml_functions.c' || echo './'`xml_functions.c; \
        then mv -f ".deps/splashy_config-xml_functions.Tpo" ".deps/splashy_config-xml_functions.Po"; else rm -f ".deps/splashy_config-xml_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_config.o -MD -MP -MF ".deps/splashy_config-xml_config.Tpo" -c -o splashy_config-xml_config.o `test -f 'xml_config.c' || echo './'`xml_config.c; \
        then mv -f ".deps/splashy_config-xml_config.Tpo" ".deps/splashy_config-xml_config.Po"; else rm -f ".deps/splashy_config-xml_config.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-common_functions.o -MD -MP -MF ".deps/splashy_config-common_functions.Tpo" -c -o splashy_config-common_functions.o `test -f 'common_functions.c' || echo './'`common_functions.c; \
        then mv -f ".deps/splashy_config-common_functions.Tpo" ".deps/splashy_config-common_functions.Po"; else rm -f ".deps/splashy_config-common_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_config-xml_parser.o -MD -MP -MF ".deps/splashy_config-xml_parser.Tpo" -c -o splashy_config-xml_parser.o `test -f 'xml_parser.c' || echo './'`xml_parser.c; \
        then mv -f ".deps/splashy_config-xml_parser.Tpo" ".deps/splashy_config-xml_parser.Po"; else rm -f ".deps/splashy_config-xml_parser.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS   -o splashy_config -static -all_load  /usr/lib/libglib-2.0.a /usr/lib/libmagic.a /usr/lib/libz.a splashy_config-splashy_config-main.o splashy_config-splashy_config-functions.o splashy_config-xml_functions.o splashy_config-xml_config.o splashy_config-common_functions.o splashy_config-xml_parser.o
gcc -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -o splashy_config -all_load splashy_config-splashy_config-main.o splashy_config-splashy_config-functions.o splashy_config-xml_functions.o splashy_config-xml_config.o splashy_config-common_functions.o splashy_config-xml_parser.o  /usr/lib/libglib-2.0.a /usr/lib/libmagic.a /usr/lib/libz.a
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-splashy_update.o -MD -MP -MF ".deps/splashy_update-splashy_update.Tpo" -c -o splashy_update-splashy_update.o `test -f 'splashy_update.c' || echo './'`splashy_update.c; \
        then mv -f ".deps/splashy_update-splashy_update.Tpo" ".deps/splashy_update-splashy_update.Po"; else rm -f ".deps/splashy_update-splashy_update.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-xml_config.o -MD -MP -MF ".deps/splashy_update-xml_config.Tpo" -c -o splashy_update-xml_config.o `test -f 'xml_config.c' || echo './'`xml_config.c; \
        then mv -f ".deps/splashy_update-xml_config.Tpo" ".deps/splashy_update-xml_config.Po"; else rm -f ".deps/splashy_update-xml_config.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-common_functions.o -MD -MP -MF ".deps/splashy_update-common_functions.Tpo" -c -o splashy_update-common_functions.o `test -f 'common_functions.c' || echo './'`common_functions.c; \
        then mv -f ".deps/splashy_update-common_functions.Tpo" ".deps/splashy_update-common_functions.Po"; else rm -f ".deps/splashy_update-common_functions.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_update-xml_parser.o -MD -MP -MF ".deps/splashy_update-xml_parser.Tpo" -c -o splashy_update-xml_parser.o `test -f 'xml_parser.c' || echo './'`xml_parser.c; \
        then mv -f ".deps/splashy_update-xml_parser.Tpo" ".deps/splashy_update-xml_parser.Po"; else rm -f ".deps/splashy_update-xml_parser.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS   -o splashy_update  /usr/lib/libglib-2.0.a splashy_update-splashy_update.o splashy_update-xml_config.o splashy_update-common_functions.o splashy_update-xml_parser.o
gcc -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -o splashy_update splashy_update-splashy_update.o splashy_update-xml_config.o splashy_update-common_functions.o splashy_update-xml_parser.o  /usr/lib/libglib-2.0.a
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -D_REENTRANT -D_GNU_SOURCE -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/directfb   -I/usr/include/directfb -D_REENTRANT -L/usr/lib/directfb-0.9.24/inputdrivers    -g -O2 -Wall -Werror -DG_DISABLE_ASSERT -DG_DISABLE_CHECKS -MT splashy_pgrep-splashy_pgrep.o -MD -MP -MF ".deps/splashy_pgrep-splashy_pgrep.Tpo" -c -o splashy_pgrep-splashy_pgrep.o `test -f 'splashy_pgrep.c' || echo './'`splashy_pgrep.c; \
        then mv -f ".deps/splashy_pgrep-splashy_pgrep.Tpo" ".deps/splashy_pgrep-splashy_pgrep.Po"; else rm -f ".deps/splashy_pgrep-splashy_pgrep.Tpo"; exit 1; fi
splashy_pgrep.c:30:27: error: proc/readproc.h: No such file or directory
splashy_pgrep.c:31:22: error: proc/sig.h: No such file or directory
splashy_pgrep.c:32:26: error: proc/devname.h: No such file or directory
splashy_pgrep.c:33:26: error: proc/sysinfo.h: No such file or directory
splashy_pgrep.c:34:47: error: proc/version.h: No such file or directory
splashy_pgrep.c: In function &#8216;usage&#8217;:
splashy_pgrep.c:65: error: expected declaration specifiers before &#8216;NORETURN&#8217;
splashy_pgrep.c:67: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
splashy_pgrep.c:80: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;str&#8217;
splashy_pgrep.c:124: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;str&#8217;
splashy_pgrep.c:147: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:166: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:185: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:199: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:213: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:225: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;name&#8217;
splashy_pgrep.c:233: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;list&#8217;
splashy_pgrep.c:249: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;value&#8217;
splashy_pgrep.c:265: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;list&#8217;
splashy_pgrep.c:276: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;list&#8217;
splashy_pgrep.c:287: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
splashy_pgrep.c:320: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
splashy_pgrep.c:352: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
splashy_pgrep.c:479: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
splashy_pgrep.c:610: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
splashy_pgrep.c:631: error: expected &#8216;{&#8217; at end of input
make[2]: *** [splashy_pgrep-splashy_pgrep.o] Error 1
make[2]: Leaving directory `/home/user/Downloads/splashy-0.2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/Downloads/splashy-0.2.1'
make: *** [all] Error 2

```

Anyone who can help?

---

### Post by compwiz18 on 2006-12-16
We must be missing a library or something...

But I don't know what it would be.

---

