---
title: "Make/GCC consistantly segfaults"
date: 2007-07-20
forum: General Help
---

### Post by skd5aner on 2007-07-20
I'm having an issue where running make/gcc on feisty crashes & segfaults randomly while trying to compile source.  I can reboot the machine, and generally it'll start to compile where it left off for a little bit, then segfault again.  Occasionally I can just type "make" again and it'll continue where it left off.  Here's an example while compiling mythtv:

```
ccache g++ -c -pipe -march=k8 -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -fomit-frame-pointer -O3 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -Wno-non-virtual-dtor -D__STDC_CONSTANT_MACROS -fomit-frame-pointer -I/usr/include/freetype2 -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr/local\" -DLIBDIR=\"/usr/local/lib\" -D_LARGEFILE_SOURCE -DUSING_OSS -DUSING_H264TOOLS -DUSING_XV -DUSING_XVMC -DUSING_XVMC_PBUFFER -DUSING_OPENGL -DUSING_XVMC_OPENGL -DUSING_OPENGL_VSYNC -DUSING_FRONTEND -DUSING_V4L -DUSING_LINUX_FIREWIRE -DUSING_FIREWIRE -DUSING_LIBAVC_5_3 -DUSING_DBOX2 -DUSING_IPTV -DUSING_HDHOMERUN -DUSING_IVTV -DUSING_DVB -DUSING_BACKEND -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../../../../../local/include -I../../../../../include -I../.. -I.. -I../libmyth -I../libavcodec -I../libavutil -I../libmythmpeg2 -Idvbdev -Impeg -Iiptv -I../libmythlivemedia/BasicUsageEnvironment/include -I../libmythlivemedia/groupsock/include -I../libmythlivemedia/liveMedia/include -I../libmythlivemedia/UsageEnvironment/include -I../../../../../include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o programinfo.o programinfo.cpp
programinfo.cpp: In member function âvoid ProgramInfo::ToMap(QMap<QString, QString>&, bool) constâ:
programinfo.cpp:447: internal compiler error: in expand_gimple_cond_expr, at cfgexpand.c:1134
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[2]: *** [programinfo.o] Error 1
make[2]: Leaving directory `/usr/src/mythtv/mythtv/libs/libmythtv'
make[1]: *** [sub-libmythtv] Error 2
make[1]: Leaving directory `/usr/src/mythtv/mythtv/libs'
make: *** [sub-libs] Error 2

```

any ideas?

---

