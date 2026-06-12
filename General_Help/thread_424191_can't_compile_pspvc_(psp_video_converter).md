---
title: "can't compile pspvc (psp video converter)"
date: 2007-04-26
forum: General Help
---

### Post by pdrift on 2007-04-26
hi, i keep getting this error when i try to compile pspvc, a video converter for my psp which i had working awesomely in edgy.
heres what i get at the terminal:

pdrift@mybu:~$ cd Desktop
pdrift@mybu:~/Desktop$ cd pspvc-install.0.3
bash: cd: pspvc-install.0.3: No such file or directory
pdrift@mybu:~/Desktop$ cd pspvc-install-0.3
pdrift@mybu:~/Desktop/pspvc-install-0.3$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libemeraldengine0 libberyldecoration0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pdrift@mybu:~/Desktop/pspvc-install-0.3$ make
make: *** No targets specified and no makefile found.  Stop.
pdrift@mybu:~/Desktop/pspvc-install-0.3$    ./configure
bash: ./configure: No such file or directory
pdrift@mybu:~/Desktop/pspvc-install-0.3$ ./configure
bash: ./configure: No such file or directory
pdrift@mybu:~/Desktop/pspvc-install-0.3$ make  
make: *** No targets specified and no makefile found.  Stop.
pdrift@mybu:~/Desktop/pspvc-install-0.3$ sudo make install
cat install.sh >install 
chmod a+x install
pdrift@mybu:~/Desktop/pspvc-install-0.3$ ./install /usr/local
X264 of PSPVC package already install
Installer force X264 installation
x264-svn/
x264-svn/matroska.h
x264-svn/configure
x264-svn/Makefile
x264-svn/matroska.c
x264-svn/doc/
x264-svn/doc/vui.txt
x264-svn/doc/ratecontrol.txt
x264-svn/doc/regression_test.txt
x264-svn/tools/
x264-svn/tools/checkasm.c
x264-svn/tools/avc2avi.c
x264-svn/tools/.cvsignore
x264-svn/tools/Jamfile
x264-svn/tools/countquant_x264.pl
x264-svn/tools/x264-rd.sh
x264-svn/tools/xyuv.c
x264-svn/tools/q_matrix_jvt.cfg
x264-svn/extras/
x264-svn/extras/getopt.h
x264-svn/extras/getopt.c
x264-svn/extras/stdint.h
x264-svn/gtk/
x264-svn/gtk/x264_gtk_i18n.h
x264-svn/gtk/x264_gtk_encode_status_window.h
x264-svn/gtk/x264.ico
x264-svn/gtk/x264_gtk_bitrate.c
x264-svn/gtk/x264_gtk_bitrate.h
x264-svn/gtk/Makefile
x264-svn/gtk/x264_gtk_encode_private.h
x264-svn/gtk/fr.po
x264-svn/gtk/x264_gtk_encode_encode.c
x264-svn/gtk/x264_gtk_encode_encode.h
x264-svn/gtk/x264_gtk_rc.c
x264-svn/gtk/x264_gtk_encode.c
x264-svn/gtk/x264gtk.rc
x264-svn/gtk/x264_gtk_private.h
x264-svn/gtk/x264_gtk_encode_main_window.c
x264-svn/gtk/test.c
x264-svn/gtk/x264_gtk_rc.h
x264-svn/gtk/x264_gtk_enum.h
x264-svn/gtk/x264_gtk_more.c
x264-svn/gtk/x264_gtk_more.h
x264-svn/gtk/x264_gtk_cqm.c
x264-svn/gtk/x264_gtk_encode_main_window.h
x264-svn/gtk/x264_gtk_cqm.h
x264-svn/gtk/x264_gtk.c
x264-svn/gtk/x264.png
x264-svn/gtk/x264_gtk_mb.h
x264-svn/gtk/x264_gtk_demuxers.h
x264-svn/gtk/x264_gtk.h
x264-svn/gtk/x264_gtk_mb.c
x264-svn/gtk/x264_gtk_encode_status_window.c
x264-svn/muxers.c
x264-svn/build/
x264-svn/build/win32/
x264-svn/build/win32/x264.dsw
x264-svn/build/win32/libx264.vcproj
x264-svn/build/win32/x264.sln
x264-svn/build/win32/x264.vcproj
x264-svn/build/win32/x264.dsp
x264-svn/build/win32/libx264.dsp
x264-svn/x264.c
x264-svn/x264.h
x264-svn/COPYING
x264-svn/encoder/
x264-svn/encoder/me.h
x264-svn/encoder/me.c
x264-svn/encoder/set.c
x264-svn/encoder/analyse.c
x264-svn/encoder/encoder.c
x264-svn/encoder/eval.c
x264-svn/encoder/analyse.h
x264-svn/encoder/macroblock.c
x264-svn/encoder/cavlc.c
x264-svn/encoder/slicetype.c
x264-svn/encoder/ratecontrol.c
x264-svn/encoder/set.h
x264-svn/encoder/macroblock.h
x264-svn/encoder/rdo.c
x264-svn/encoder/cabac.c
x264-svn/encoder/ratecontrol.h
x264-svn/common/
x264-svn/common/frame.c
x264-svn/common/pixel.h
x264-svn/common/visualize.h
x264-svn/common/set.c
x264-svn/common/dct.c
x264-svn/common/frame.h
x264-svn/common/cpu.c
x264-svn/common/macroblock.c
x264-svn/common/common.c
x264-svn/common/quant.h
x264-svn/common/visualize.c
x264-svn/common/common.h
x264-svn/common/amd64/
x264-svn/common/amd64/cpu-a.asm
x264-svn/common/amd64/mc-a.asm
x264-svn/common/amd64/pixel-a.asm
x264-svn/common/amd64/deblock-a.asm
x264-svn/common/amd64/dct-a.asm
x264-svn/common/amd64/mc-a2.asm
x264-svn/common/amd64/amd64inc.asm
x264-svn/common/amd64/pixel-sse2.asm
x264-svn/common/amd64/quant-a.asm
x264-svn/common/amd64/predict-a.asm
x264-svn/common/dct.h
x264-svn/common/mc.h
x264-svn/common/bs.h
x264-svn/common/display.h
x264-svn/common/quant.c
x264-svn/common/display-x11.c
x264-svn/common/mdate.c
x264-svn/common/predict.h
x264-svn/common/i386/
x264-svn/common/i386/cpu-a.asm
x264-svn/common/i386/mc-a.asm
x264-svn/common/i386/pixel.h
x264-svn/common/i386/pixel-a.asm
x264-svn/common/i386/deblock-a.asm
x264-svn/common/i386/mc-c.c
x264-svn/common/i386/dct-a.asm
x264-svn/common/i386/quant.h
x264-svn/common/i386/mc-a2.asm
x264-svn/common/i386/pixel-sse2.asm
x264-svn/common/i386/dct.h
x264-svn/common/i386/mc.h
x264-svn/common/i386/predict.h
x264-svn/common/i386/quant-a.asm
x264-svn/common/i386/predict-c.c
x264-svn/common/i386/i386inc.asm
x264-svn/common/i386/predict-a.asm
x264-svn/common/cabac.h
x264-svn/common/csp.c
x264-svn/common/set.h
x264-svn/common/predict.c
x264-svn/common/csp.h
x264-svn/common/clip1.h
x264-svn/common/sparc/
x264-svn/common/sparc/pixel.h
x264-svn/common/sparc/pixel.asm
x264-svn/common/ppc/
x264-svn/common/ppc/pixel.h
x264-svn/common/ppc/ppccommon.h
x264-svn/common/ppc/dct.c
x264-svn/common/ppc/dct.h
x264-svn/common/ppc/mc.h
x264-svn/common/ppc/pixel.c
x264-svn/common/ppc/mc.c
x264-svn/common/pixel.c
x264-svn/common/mc.c
x264-svn/common/macroblock.h
x264-svn/common/vlc.h
x264-svn/common/cabac.c
x264-svn/common/cpu.h
x264-svn/version.sh
x264-svn/muxers.h
x264-svn/config.guess
x264-svn/AUTHORS
./version.sh: 2: svnversion: not found
Platform:   X86
System:     LINUX
avis input: no
mp4 output: no
pthread:    yes
gtk:        no
debug:      no
gprof:      no
PIC:        no
shared:     no
visualize:  no

You can run 'make' or 'make fprofiled' now.
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o x264.o x264.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o matroska.o matroska.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o muxers.o muxers.c
rm -f .depend
( echo -n "`dirname common/mc.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/csp.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/csp.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/mc-c.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/i386/mc-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/predict-c.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer common/i386/predict-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer matroska.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname muxers.c`/" && gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer muxers.c -MM -g0 ) 1>> .depend;
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mc.o common/mc.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/predict.o common/predict.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/pixel.o common/pixel.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/macroblock.o common/macroblock.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/frame.o common/frame.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/dct.o common/dct.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cpu.o common/cpu.c
common/cpu.c: In function ‘x264_cpu_num_processors’:
common/cpu.c:172: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cabac.o common/cabac.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/common.o common/common.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mdate.o common/mdate.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/csp.o common/csp.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/set.o common/set.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/quant.o common/quant.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/analyse.o encoder/analyse.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/me.o encoder/me.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/ratecontrol.o encoder/ratecontrol.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/set.o encoder/set.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/macroblock.o encoder/macroblock.c
encoder/macroblock.c: In function ‘x264_mb_encode_8x8_chroma’:
encoder/macroblock.c:301: warning: dereferencing type-punned pointer will break strict-aliasing rules
encoder/macroblock.c: In function ‘x264_macroblock_encode_p8x8’:
encoder/macroblock.c:843: warning: dereferencing type-punned pointer will break strict-aliasing rules
encoder/macroblock.c:871: warning: dereferencing type-punned pointer will break strict-aliasing rules
encoder/macroblock.c:892: warning: dereferencing type-punned pointer will break strict-aliasing rules
encoder/macroblock.c: In function ‘x264_macroblock_probe_skip’:
encoder/macroblock.c:670: warning: ‘mvp[0]’ may be used uninitialized in this function
encoder/macroblock.c:670: warning: ‘mvp[1]’ may be used uninitialized in this function
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cabac.o encoder/cabac.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cavlc.o encoder/cavlc.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/encoder.o encoder/encoder.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/eval.o encoder/eval.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/i386/mc-c.o common/i386/mc-c.c
gcc -O4 -ffast-math -Wall -I. -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/i386/predict-c.o common/i386/predict-c.c
nasm -O2 -f elf -Icommon/i386/ -o common/i386/dct-a.o common/i386/dct-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/cpu-a.o common/i386/cpu-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/pixel-a.o common/i386/pixel-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/mc-a.o common/i386/mc-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/mc-a2.o common/i386/mc-a2.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/predict-a.o common/i386/predict-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/pixel-sse2.o common/i386/pixel-sse2.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/quant-a.o common/i386/quant-a.asm
nasm -O2 -f elf -Icommon/i386/ -o common/i386/deblock-a.o common/i386/deblock-a.asm
ar rc libx264.a common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/mdate.o common/csp.o common/set.o common/quant.o encoder/analyse.o encoder/me.o encoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/cavlc.o encoder/encoder.o encoder/eval.o common/i386/mc-c.o common/i386/predict-c.o common/i386/dct-a.o common/i386/cpu-a.o common/i386/pixel-a.o common/i386/mc-a.o common/i386/mc-a2.o common/i386/predict-a.o common/i386/pixel-sse2.o common/i386/quant-a.o common/i386/deblock-a.o
ranlib libx264.a
gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -s
install -d /usr/local/share/pspvc/bin /usr/local/share/pspvc/include
install -d /usr/local/share/pspvc/lib /usr/local/share/pspvc/lib/pkgconfig
install -m 644 x264.h /usr/local/share/pspvc/include
install: cannot remove `/usr/local/share/pspvc/include/x264.h': Permission denied
make: *** [install] Error 1
-e \E[01;31mERROR during compilation or installation of X264
pdrift@mybu:~/Desktop/pspvc-install-0.3$

---

### Post by pdrift on 2007-04-27
does anyone have any ideas what going wrong here?

it says:
 install: cannot remove `/usr/local/share/pspvc/include/x264.h': Permission denied
make: *** [install] Error 1

does this mean i'm not root? i don't understand it.
when i try to log in as right by typing su then my password, it says
authentication failure. but i now i;m tyoing in the correct password

a little help would be very much appreciated.

---

### Post by bsheep on 2007-04-27
Under Feisty, I've just installed the deps with the following commands :

sudo apt-get install nasm libfaac-dev libxvidcore-dev
sudo apt-get install libgtk2.0-dev

and the pspvc directory sudo ./install.sh

---

### Post by pdrift on 2007-04-27
thanks for the tip. i found another thread last night and managed to install
the program and it went through without a hitch.
 i got these directions from jimrockfords thread [http://ubuntuforums.org/showthread.php?t=359361](http://ubuntuforums.org/showthread.php?t=359361)
so let me say thank you to him. 
 here are the instrutctions i followed:

   pspvc install help
 
   1. Download pspvc from here: [http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/), saving it to your desktop.

   2. Double click the pspvc tar.gz file on your desktop.

   3. Press "Extract", ensure "Desktop" is listed as the location to extract the files, and then                         press the "Extract" button (again).

   4. You should now have a pspvc-install-0.2.1 folder on your desktop.

   5. Open Terminal or Konsole (whichever you have installed).
 
   6. Install dependencies using this command:
   Code:

   sudo apt-get install libgtk2.0-dev libfaac-dev libxvidcore4-dev nasm build-essential

   7. Several development libraries that pspvc requires will install. You'll see a bunch of output    and it'll take a few seconds to complete.

   8. Next, enter the following command, replacing user with your user name. This will change  the prompt to the pspvc installation directory.
Code:

   cd /home/user/Desktop/pspvc-install-0.2.1

   9. To begin the pspvc install, enter this command:
   Code:

   sudo ./install.sh

   10. When the install completes, you should see a message that says "PSPVC installation   completed". You're done!

it worked for me. but thanks anyways.

---

### Post by Devezu on 2007-07-04
I had a similar problem but now, how do you launch pspvc?

---

### Post by anjilslaire on 2007-07-07
I just got my psp this week. pdrift's instructions worked perfectly.
After install, I found it in Multimedia on my Kubuntu menu. You can also start it from terminal with:
pspvc
Time to load OE 3.40-A .....

---

