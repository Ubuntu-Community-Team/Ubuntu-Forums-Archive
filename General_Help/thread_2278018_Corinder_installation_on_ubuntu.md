---
title: "Corinder installation on ubuntu"
date: 2015-05-13
forum: General Help
---

### Post by shahnawaz3 on 2015-05-13
I am trying to install **Coriander** on Ubuntu, but when I tried to make it I got the following error:

```
make  all-recursive
make[1]: Entering directory `/home/ubuntu/Downloads/coriander-2.0.0'
Making all in po
make[2]: Entering directory `/home/ubuntu/Downloads/coriander-2.0.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ubuntu/Downloads/coriander-2.0.0/po'
Making all in src
make[2]: Entering directory `/home/ubuntu/Downloads/coriander-2.0.0/src'
gcc  -g -O2   -o coriander main.o support.o interface.o error.o definitions.o camera.o thread_base.o thread_iso.o watch_thread.o SDLEvent.o thread_display.o thread_ftp.o thread_save.o thread_v4l.o tools.o conversions.o callbacks.o update_frames.o build_frames.o update_windows.o build_windows.o build_menus.o update_ranges.o build_ranges.o preferences.o video_encode.o subtitles.o -L/usr/X11R6/lib/ -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfontconfig -lfreetype -lgconf-2 -lgthread-2.0 -lgmodule-2.0 -lgobject-2.0 -lglib-2.0    -lftp -L/usr/lib/arm-linux-gnueabihf -lSDL -ldc1394 -lraw1394 -lXv  -lgthread-2.0  
/usr/bin/ld: tools.o: undefined reference to symbol 'XOpenDisplay'
//usr/lib/arm-linux-gnueabihf/libX11.so.6: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make[2]: *** [coriander] Error 1
make[2]: Leaving directory `/home/ubuntu/Downloads/coriander-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubuntu/Downloads/coriander-2.0.0'
make: *** [all] Error 2
```

I am not able to figure this out. I am trying to use firewire 1394 camera with nvidia tegra tk1 installed with Ubuntu.

---

