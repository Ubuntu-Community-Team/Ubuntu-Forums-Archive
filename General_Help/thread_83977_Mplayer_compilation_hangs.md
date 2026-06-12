---
title: "Mplayer compilation hangs"
date: 2005-10-30
forum: General Help
---

### Post by mike_w on 2005-10-30
I went thru all this dependency stuff. I have gcc 3.4, libgtk1.2-devel anyway; ./configure went smoothly but one thing: it didn't recognized my gcc version so I disbaled checking.

Then now when I'm issuing make command it says:

make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/mike/DEB/MPlayer-1.0pre7try2/libavcodec'
cc -I../libvo -I../../libvo  -fno-PIC -O4 -march=athlon-4 -mcpu=athlon-4 -pipe -ffast-math -fomit-frame-pointer -D_REENTRANT -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE  -c -o libpostproc/postprocess.o libpostproc/postprocess.c
make[1]: cc: Command not found
make[1]: *** [libpostproc/postprocess.o] Error 127
make[1]: Leaving directory `/home/mike/DEB/MPlayer-1.0pre7try2/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2

:???:   So, any ideas what is wrong?

Thanks in advance.

---

### Post by mike_w on 2005-11-26
This helped:

[http://ubuntuforums.org/showthread.php?t=83595&highlight=mplayer+patch](http://ubuntuforums.org/showthread.php?t=83595&highlight=mplayer+patch)

So the problem is solved.

---

