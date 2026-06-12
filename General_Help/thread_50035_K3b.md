---
title: "K3b"
date: 2005-07-18
forum: General Help
---

### Post by michellembrodeur on 2005-07-18
Hi all

This is the error when I try to install the lastest version of K3B
"/bin/sh ../../../libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o libk3bffmpegdecoder.la -rpath /usr/lib/kde3 -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib    k3bffmpegdecoder.lo k3bffmpegwrapper.lo ../../../libk3b/libk3b.la -lkdeui -lavcodec -lavformat -lm -L/usr/lib -L/usr/share/qt3/lib -L/usr/X11R6/lib
/usr/lib/libavformat.a(utils.o)(.text+0x1ad1): In function `av_find_stream_info':
: undefined reference to `avcodec_pix_fmt_to_codec_tag'
/usr/lib/libavformat.a(allformats.o)(.text+0x24): In function `av_register_all':
: undefined reference to `avcodec_register_all'
/usr/lib/libavformat.a(ogg.o)(.text+0x44): In function `ogg_write_header':
: undefined reference to `ogg_stream_init'
/usr/lib/libavformat.a(ogg.o)(.text+0x100): In function `ogg_write_header':
: undefined reference to `ogg_stream_packetin'
/usr/lib/libavformat.a(ogg.o)(.text+0x189): In function `ogg_write_packet':
: undefined reference to `ogg_stream_flush'
/usr/lib/libavformat.a(ogg.o)(.text+0x208): In function `ogg_write_packet':
: undefined reference to `ogg_stream_packetin'
/usr/lib/libavformat.a(ogg.o)(.text+0x21d): In function `ogg_write_packet':
: undefined reference to `ogg_stream_pageout'
/usr/lib/libavformat.a(ogg.o)(.text+0x28a): In function `ogg_write_trailer':
: undefined reference to `ogg_stream_flush'
/usr/lib/libavformat.a(ogg.o)(.text+0x2cc): In function `ogg_write_trailer':
: undefined reference to `ogg_stream_clear'
/usr/lib/libavformat.a(ogg.o)(.text+0x2f3): In function `ogg_read_header':
: undefined reference to `ogg_sync_init'
/usr/lib/libavformat.a(ogg.o)(.text+0x303): In function `ogg_read_header':
: undefined reference to `ogg_sync_buffer'
/usr/lib/libavformat.a(ogg.o)(.text+0x340): In function `ogg_read_header':
: undefined reference to `ogg_sync_wrote'
/usr/lib/libavformat.a(ogg.o)(.text+0x34c): In function `ogg_read_header':
: undefined reference to `ogg_sync_pageout'
/usr/lib/libavformat.a(ogg.o)(.text+0x354): In function `ogg_read_header':
: undefined reference to `ogg_page_serialno'
/usr/lib/libavformat.a(ogg.o)(.text+0x360): In function `ogg_read_header':
: undefined reference to `ogg_stream_init'
/usr/lib/libavformat.a(ogg.o)(.text+0x36c): In function `ogg_read_header':
: undefined reference to `ogg_stream_pagein'
/usr/lib/libavformat.a(ogg.o)(.text+0x3e4): In function `ogg_read_header':
: undefined reference to `ogg_stream_packetout'
/usr/lib/libavformat.a(ogg.o)(.text+0x3fe): In function `ogg_read_header':
: undefined reference to `ogg_sync_pageout'
/usr/lib/libavformat.a(ogg.o)(.text+0x413): In function `ogg_read_header':
: undefined reference to `ogg_sync_buffer'
/usr/lib/libavformat.a(ogg.o)(.text+0x43e): In function `ogg_read_header':
: undefined reference to `ogg_sync_wrote'
/usr/lib/libavformat.a(ogg.o)(.text+0x45b): In function `ogg_read_header':
: undefined reference to `ogg_stream_pagein'
/usr/lib/libavformat.a(ogg.o)(.text+0x500): In function `ogg_read_packet':
: undefined reference to `ogg_stream_packetout'
/usr/lib/libavformat.a(ogg.o)(.text+0x521): In function `ogg_read_packet':
: undefined reference to `ogg_sync_pageout'
/usr/lib/libavformat.a(ogg.o)(.text+0x536): In function `ogg_read_packet':
: undefined reference to `ogg_sync_buffer'
/usr/lib/libavformat.a(ogg.o)(.text+0x561): In function `ogg_read_packet':
: undefined reference to `ogg_sync_wrote'
/usr/lib/libavformat.a(ogg.o)(.text+0x581): In function `ogg_read_packet':
: undefined reference to `ogg_stream_pagein'
/usr/lib/libavformat.a(ogg.o)(.text+0x63b): In function `ogg_read_close':
: undefined reference to `ogg_stream_clear'
/usr/lib/libavformat.a(ogg.o)(.text+0x643): In function `ogg_read_close':
: undefined reference to `ogg_sync_clear'
collect2: ld returned 1 exit status
make[4]: *** [libk3bffmpegdecoder.la] Error 1
make[4]: Leaving directory `/home/michelle/k3b-0.12.2/plugins/decoder/ffmpeg'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/michelle/k3b-0.12.2/plugins/decoder'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/michelle/k3b-0.12.2/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/michelle/k3b-0.12.2'
make: *** [all] Error 2
"

I have the ltest QT files, dvd+rw tools,  cdrtools, etc. Everything the guide says.

Also tried uninstalling libavformat and reinstalling. Anyone have a clue, and if so, what do I need to do?

thanks all

---

### Post by jfdill_2 on 2005-08-22
Hmm I'm getting the same error trying to compile ZoneMinder, which does not depend on Qt, so I'm thinking it's ogg vorbis related.  I'll post the solution in a sec if I figure it out.

---

### Post by arnieboy on 2005-08-23
Try removing libavcodec-dev and libavformat-dev if installed
and try compiling again.

---

### Post by jfdill_2 on 2005-08-23
[QUOTE=arnieboy]Try removing libavcodec-dev and libavformat-dev if installed
and try compiling again.[/QUOTE]
Tried it, no luck yet.  ZM seems to want some stuff from the ffmpeg package that doesn't jibe with the ffmpeg packages from the repository.  Right now I'm trying to build ffmpeg from the CVS, but ZM still doesn't like the results.  I'll try the ZM forum for help with that.

NM  :oops:  I needed to add /usr/local/lib to /etc/ld.so.conf and run ldconfig, then all was happy :D thanks for the hint.

---

