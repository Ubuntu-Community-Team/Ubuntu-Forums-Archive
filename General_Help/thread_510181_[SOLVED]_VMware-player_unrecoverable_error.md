---
title: "[SOLVED] VMware-player unrecoverable error"
date: 2007-07-26
forum: General Help
---

### Post by rangalo on 2007-07-26
Hi,

I am new to Ubuntu linux. I just installed Feisty Fawn (7.04) 2 weeks ago.  After that I dist-upgraded atleast 2 times.

I installed vmware-player. When I start vmplayer from commandline, it crashes with the unrecoverable error and following log file.

What should I do ? I also tried vmware before some time and the player was working well. Did dist-upgrade break it ?

Any ideas ? 

PS: I am using fluxbox instead of kde.

regards,
Hardik

Here the log file.
```

Jul 26 16:16:41: vmplayer| Log for VMware Player pid=5900 version=1.0.2 build=build-29634 option=Release
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-xpm.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:41: vmplayer| Using log file /tmp/vmware-hardik/player-5900.log
Jul 26 16:16:41: vmplayer| HAL04LoadHALLibraries: Could not dlopen libhal.so.0.
Jul 26 16:16:41: vmplayer| HAL05LoadHALLibraries: Could not dlopen libdbus-1.so.1 or libdbus-1.so.2.
Jul 26 16:16:42: vmplayer| Msg_Reset:
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/site license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.License.cantOpenDirectory] Unable to open the /usr/lib/vmware-player/licenses/user license directory: No such file or directory
Jul 26 16:16:42: vmplayer| [msg.dictionary.load.statFailed] Unable to get information about file "/usr/lib/vmware-player/messages/en/tip_list.vmsg": No such file or directory.
Jul 26 16:16:42: vmplayer| ----------------------------------------
Jul 26 16:16:42: vmplayer| Cannot load message dictionary "/usr/lib/vmware-player/messages/en/tip_list.vmsg".
Jul 26 16:16:42: vmplayer| SMBIOS: can't open /dev/mem
Jul 26 16:16:42: vmplayer| VmhsHostInfoPopulateSystem:  Could not get information from smbios to populate VMDB.
Jul 26 16:16:42: vmplayer| HOSTINFO: Seeing Intel CPU, numCoresPerCPU 1 numThreadsPerCore 2.
Jul 26 16:16:42: vmplayer| HOSTINFO: This machine has 1 physical CPUS, 1 total cores, and 2 logical CPUs.
Jul 26 16:16:42: vmplayer| Using system libcrypto, version 9070BF
Jul 26 16:16:42: vmplayer| Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Jul 26 16:16:43: vmplayer| (null): No builtin or dynamically loaded modules
Jul 26 16:16:43: vmplayer| were found. Pango will not work correctly. This probably means
Jul 26 16:16:43: vmplayer| there was an error in the creation of:
Jul 26 16:16:43: vmplayer|   '/usr/etc/pango/pango.modules'
Jul 26 16:16:43: vmplayer| You may be able to recreate this file by running pango-querymodules.
Jul 26 16:16:43: vmplayer| GLib-GObject: file ../../glib-2.4.8/gobject/gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed
Jul 26 16:16:43: vmplayer| (null): file ../../pango-1.4.1/pango/pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed
Jul 26 16:16:43: vmplayer| (null): file ../../pango-1.4.1/pango/shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
Jul 26 16:16:43: vmplayer| Backtrace:
Jul 26 16:16:43: vmplayer| Backtrace[0] 0xbf846b38 eip 0x809fb40 
Jul 26 16:16:43: vmplayer| Backtrace[1] 0xbf846f58 eip 0x8096b75 
Jul 26 16:16:43: vmplayer| Backtrace[2] 0xbf846f78 eip 0x8063038 
Jul 26 16:16:43: vmplayer| Backtrace[3] 0xbf846f98 eip 0x8284f5b 
Jul 26 16:16:43: vmplayer| Backtrace[4] 0xbf847418 eip 0xb7ce7bcc 
Jul 26 16:16:43: vmplayer| Backtrace[5] 0xbf847438 eip 0xb7ce7c7a 
Jul 26 16:16:43: vmplayer| Backtrace[6] 0xbf847468 eip 0xb7c3b274 
Jul 26 16:16:43: vmplayer| Backtrace[7] 0xbf847508 eip 0xb7c316a5 
Jul 26 16:16:43: vmplayer| Backtrace[8] 0xbf847578 eip 0xb7c31cca 
Jul 26 16:16:43: vmplayer| Backtrace[9] 0xbf847618 eip 0xb7c32648 
Jul 26 16:16:43: vmplayer| Backtrace[10] 0xbf8476e8 eip 0xb7c30340 
Jul 26 16:16:43: vmplayer| Backtrace[11] 0xbf847718 eip 0xb7c307a7 
Jul 26 16:16:43: vmplayer| Backtrace[12] 0xbf847778 eip 0xb7bef389 
Jul 26 16:16:43: vmplayer| Backtrace[13] 0xbf847788 eip 0xb7c221e4 
Jul 26 16:16:43: vmplayer| Backtrace[14] 0xbf8477d8 eip 0xb7c3359b 
Jul 26 16:16:43: vmplayer| Backtrace[15] 0xbf8478a8 eip 0xb7c33d76 
Jul 26 16:16:43: vmplayer| Backtrace[16] 0xbf847918 eip 0xb7c30211 
Jul 26 16:16:43: vmplayer| Backtrace[17] 0xbf8479e8 eip 0xb7c30458 
Jul 26 16:16:43: vmplayer| Backtrace[18] 0xbf847a18 eip 0xb7c307a7 
Jul 26 16:16:43: vmplayer| Backtrace[19] 0xbf847b18 eip 0xb79e34d1 
Jul 26 16:16:43: vmplayer| Backtrace[20] 0xbf847b58 eip 0xb79e13c4 
Jul 26 16:16:43: vmplayer| Backtrace[21] 0xbf847b78 eip 0xb79e04f5 
Jul 26 16:16:43: vmplayer| Backtrace[22] 0xbf847ba8 eip 0xb79c683a 
Jul 26 16:16:43: vmplayer| Backtrace[23] 0xbf847c08 eip 0xb79e106f 
Jul 26 16:16:43: vmplayer| Backtrace[24] 0xbf847c88 eip 0xb79f3afa 
Jul 26 16:16:43: vmplayer| Backtrace[25] 0xbf847d08 eip 0xb79fa325 
Jul 26 16:16:43: vmplayer| Backtrace[26] 0xbf847d58 eip 0xb79f9e7f 
Jul 26 16:16:43: vmplayer| Backtrace[27] 0xbf847d88 eip 0xb7565737 
Jul 26 16:16:43: vmplayer| Backtrace[28] 0xbf847dc8 eip 0xb79398d1 
Jul 26 16:16:43: vmplayer| Backtrace[29] 0xbf847df8 eip 0xb7c793a1 
Jul 26 16:16:43: vmplayer| Backtrace[30] 0xbf847e48 eip 0xb7c79076 
Jul 26 16:16:43: vmplayer| Backtrace[31] 0xbf847f68 eip 0xb7c90d24 
Jul 26 16:16:43: vmplayer| Backtrace[32] 0xbf8481e8 eip 0xb7c8fd46 
Jul 26 16:16:43: vmplayer| Backtrace[33] 0xbf848208 eip 0xb7c900b8 
Jul 26 16:16:43: vmplayer| Backtrace[34] 0xbf848248 eip 0xb7a6cbff 
Jul 26 16:16:43: vmplayer| Backtrace[35] 0xbf848288 eip 0xb7986cee 
Jul 26 16:16:43: vmplayer| Backtrace[36] 0xbf8482b8 eip 0xb74ff9c0 
Jul 26 16:16:43: vmplayer| Backtrace[37] 0xbf8482f8 eip 0xb7c9229b 
Jul 26 16:16:43: vmplayer| Backtrace[38] 0xbf848328 eip 0xb7c793a1 
Jul 26 16:16:43: vmplayer| Backtrace[39] 0xbf848378 eip 0xb7c79076 
Jul 26 16:16:43: vmplayer| Backtrace[40] 0xbf848498 eip 0xb7c906eb 
Jul 26 16:16:43: vmplayer| Backtrace[41] 0xbf848718 eip 0xb7c8fd46 
Jul 26 16:16:43: vmplayer| Backtrace[42] 0xbf848738 eip 0xb7c900b8 
Jul 26 16:16:43: vmplayer| Backtrace[43] 0xbf848778 eip 0xb7898f4e 
Jul 26 16:16:43: vmplayer| Backtrace[44] 0xbf848798 eip 0xb74fee58 
Jul 26 16:16:43: vmplayer| Backtrace[45] 0xbf8487b8 eip 0xb7544aec 
Jul 26 16:16:43: vmplayer| Backtrace[46] 0xbf8489b8 eip 0x82a75a2 
Jul 26 16:16:43: vmplayer| Backtrace[47] 0xbf848bd8 eip 0x8064153 
Jul 26 16:16:43: vmplayer| Backtrace[48] 0xbf848be8 eip 0x80696c8 
Jul 26 16:16:43: vmplayer| Backtrace[49] 0xbf848c08 eip 0xb752686a 
Jul 26 16:16:43: vmplayer| Backtrace[50] 0xbf848c38 eip 0xb7932898 
Jul 26 16:16:43: vmplayer| Backtrace[51] 0xbf848c48 eip 0xb75273c9 
Jul 26 16:16:43: vmplayer| Backtrace[52] 0xbf848c58 eip 0xb75270c4 
Jul 26 16:16:43: vmplayer| Backtrace[53] 0xbf848d18 eip 0x8062fe9 
Jul 26 16:16:43: vmplayer| Backtrace[54] 0xbf848d78 eip 0xb70a1ebc 
Jul 26 16:16:43: vmplayer| Backtrace[55] 00000000 eip 0x8062e11 
Jul 26 16:16:43: vmplayer| Msg_Post: Error
Jul 26 16:16:43: vmplayer| [msg.log.error.unrecoverable] VMware Player unrecoverable error: (vmplayer)
Jul 26 16:16:43: vmplayer| (null): file ../../pango-1.4.1/pango/shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
Jul 26 16:16:43: vmplayer| [msg.panic.haveLog] A log file is available in "/tmp/vmware-hardik/player-5900.log".  [msg.panic.requestSupport.withLog] Please request support and include the contents of the log file.  [msg.panic.requestSupport.linux] 
Jul 26 16:16:43: vmplayer| To collect files to submit to VMware support, run vm-support.
Jul 26 16:16:43: vmplayer| [msg.panic.response] We will respond on the basis of your support entitlement.
Jul 26 16:16:43: vmplayer| ----------------------------------------


```

---

### Post by RudolfMDLT on 2007-07-26
I didn't install VmWare from the repo's - I downloaded and compiled from source, so I'm not sure whether you would have this command on your system or not. open up the terminal and resetup Vmware. Your data will not be lost.

> vmware-config.pl 

or try opening up Synaptic, searching for vmware, rightclick and say, re-install.


best of luck,

Rudolf

---

### Post by rangalo on 2007-07-26
hi.

> 
vmware-config.pl


I installed it from the repos using  apt-get install vmware-player.

I also re-installed it with first removing and then installing again with apt-get, with the same result.

Should I install from sources as you did ? 
[edit] Can you write the steps you followed for that ?

thanks &  regards,
Hardik

---

### Post by rangalo on 2007-07-26
Hi,

this seems to be a known bug.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg326742.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg326742.html)

Any other ways to install and run vmplayer on ubuntu ?

thanks,
Hardik

---

### Post by rangalo on 2007-07-26
I downloaded linux version from their site and was installed without problem. It just needed to compile kernel modules.

---

