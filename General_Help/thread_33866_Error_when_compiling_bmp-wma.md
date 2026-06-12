---
title: "Error when compiling bmp-wma"
date: 2005-05-12
forum: General Help
---

### Post by twan on 2005-05-12
I get an error when trying to compile the wma plugin for beep media player..

Here's the error log:
```

make  all-recursive
make[1]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma'
make[3]: Niets te doen voor `all'.
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma'
Making all in wma123
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src/wma123'
make[3]: Niets te doen voor `all'.
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src/wma123'
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXTHREADS -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/X11R6/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0   -I./libffwma -L./libffwma -g -O2  -MT bmp-wma.lo -MD -MP -MF ".deps/bmp-wma.Tpo" -c -o bmp-wma.lo bmp-wma.c; \
then mv -f ".deps/bmp-wma.Tpo" ".deps/bmp-wma.Plo"; else rm -f ".deps/bmp-wma.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/X11R6/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I./libffwma -L./libffwma -g -O2 -MT bmp-wma.lo -MD -MP -MF .deps/bmp-wma.Tpo -c bmp-wma.c  -fPIC -DPIC -o .libs/bmp-wma.o
In file included from /usr/include/gtk-2.0/gdk/gdk.h:34,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from /usr/include/bmp/util.h:6,
                 from bmp-wma.c:30:
/usr/include/gtk-2.0/gdk/gdkdrawable.h:161: error: syntax error before "PangoMatrix"
/usr/include/gtk-2.0/gdk/gdkdrawable.h:359: error: syntax error before "PangoMatrix"
In file included from /usr/include/gtk-2.0/gdk/gdk.h:43,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from /usr/include/bmp/util.h:6,
                 from bmp-wma.c:30:
/usr/include/gtk-2.0/gdk/gdkpango.h:69: error: syntax error before "PangoRenderer"
/usr/include/gtk-2.0/gdk/gdkpango.h:72: error: syntax error before '}' token
/usr/include/gtk-2.0/gdk/gdkpango.h:84: error: syntax error before "PangoRendererClass"
/usr/include/gtk-2.0/gdk/gdkpango.h:89: error: syntax error before '*' token
/usr/include/gtk-2.0/gdk/gdkpango.h:90: error: syntax error before '*' token
/usr/include/gtk-2.0/gdk/gdkpango.h:97: error: syntax error before "PangoRenderPart"
/usr/include/gtk-2.0/gdk/gdkpango.h:100: error: syntax error before "PangoRenderPart"
In file included from /usr/include/gtk-2.0/gtk/gtkaccellabel.h:34,
                 from /usr/include/gtk-2.0/gtk/gtk.h:34,
                 from /usr/include/bmp/util.h:6,
                 from bmp-wma.c:30:
/usr/include/gtk-2.0/gtk/gtklabel.h:133: error: syntax error before "PangoEllipsizeMode"
/usr/include/gtk-2.0/gtk/gtklabel.h:134: error: syntax error before "gtk_label_get_ellipsize"
In file included from /usr/include/gtk-2.0/gtk/gtk.h:132,
                 from /usr/include/bmp/util.h:6,
                 from bmp-wma.c:30:
/usr/include/gtk-2.0/gtk/gtkprogressbar.h:144: error: syntax error before "PangoEllipsizeMode"
/usr/include/gtk-2.0/gtk/gtkprogressbar.h:145: error: syntax error before "gtk_progress_bar_get_ellipsize"
bmp-wma.c: In function `get_song_title':
bmp-wma.c:270: warning: assignment discards qualifiers from pointer target type
make[3]: *** [bmp-wma.lo] Fout 1
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
make[2]: *** [all-recursive] Fout 1
make[2]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1'
make: *** [all] Fout 2

```

I already re-installed all gtk packages with synaptic but with no result  :neutral:

---

### Post by twan on 2005-05-15
I had to reinstall ubuntu today.. so i tought i'd tried this out again:

here's the error again  :-? 

```
make  all-recursive
make[1]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1'
Making all in src
make[2]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
Making all in libffwma
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allcodecs.o -MD -MP -MF ".deps/libffwma_a-allcodecs.Tpo" -c -o libffwma_a-allcodecs.o `test -f 'allcodecs.c' || echo './'`allcodecs.c; \
then mv -f ".deps/libffwma_a-allcodecs.Tpo" ".deps/libffwma_a-allcodecs.Po"; else rm -f ".deps/libffwma_a-allcodecs.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-allformats.o -MD -MP -MF ".deps/libffwma_a-allformats.Tpo" -c -o libffwma_a-allformats.o `test -f 'allformats.c' || echo './'`allformats.c; \
then mv -f ".deps/libffwma_a-allformats.Tpo" ".deps/libffwma_a-allformats.Po"; else rm -f ".deps/libffwma_a-allformats.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-asf.o -MD -MP -MF ".deps/libffwma_a-asf.Tpo" -c -o libffwma_a-asf.o `test -f 'asf.c' || echo './'`asf.c; \
then mv -f ".deps/libffwma_a-asf.Tpo" ".deps/libffwma_a-asf.Po"; else rm -f ".deps/libffwma_a-asf.Tpo"; exit 1; fi
asf.c: In function `get_wav_header':
asf.c:249: let op: toewijzing maakt pointer van integer zonder een cast
asf.c: In function `asf_read_header':
asf.c:401: let op: toewijzing maakt pointer van integer zonder een cast
asf.c:491: let op: cast to pointer from integer of different size
asf.c:497: let op: cast to pointer from integer of different size
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-avio.o -MD -MP -MF ".deps/libffwma_a-avio.Tpo" -c -o libffwma_a-avio.o `test -f 'avio.c' || echo './'`avio.c; \
then mv -f ".deps/libffwma_a-avio.Tpo" ".deps/libffwma_a-avio.Po"; else rm -f ".deps/libffwma_a-avio.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-aviobuf.o -MD -MP -MF ".deps/libffwma_a-aviobuf.Tpo" -c -o libffwma_a-aviobuf.o `test -f 'aviobuf.c' || echo './'`aviobuf.c; \
then mv -f ".deps/libffwma_a-aviobuf.Tpo" ".deps/libffwma_a-aviobuf.Po"; else rm -f ".deps/libffwma_a-aviobuf.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-common.o -MD -MP -MF ".deps/libffwma_a-common.Tpo" -c -o libffwma_a-common.o `test -f 'common.c' || echo './'`common.c; \
then mv -f ".deps/libffwma_a-common.Tpo" ".deps/libffwma_a-common.Po"; else rm -f ".deps/libffwma_a-common.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-cutils.o -MD -MP -MF ".deps/libffwma_a-cutils.Tpo" -c -o libffwma_a-cutils.o `test -f 'cutils.c' || echo './'`cutils.c; \
then mv -f ".deps/libffwma_a-cutils.Tpo" ".deps/libffwma_a-cutils.Po"; else rm -f ".deps/libffwma_a-cutils.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-dsputil.o -MD -MP -MF ".deps/libffwma_a-dsputil.Tpo" -c -o libffwma_a-dsputil.o `test -f 'dsputil.c' || echo './'`dsputil.c; \
then mv -f ".deps/libffwma_a-dsputil.Tpo" ".deps/libffwma_a-dsputil.Po"; else rm -f ".deps/libffwma_a-dsputil.Tpo"; exit 1; fi
In file included from dsputil.c:29:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-fft.o -MD -MP -MF ".deps/libffwma_a-fft.Tpo" -c -o libffwma_a-fft.o `test -f 'fft.c' || echo './'`fft.c; \
then mv -f ".deps/libffwma_a-fft.Tpo" ".deps/libffwma_a-fft.Po"; else rm -f ".deps/libffwma_a-fft.Tpo"; exit 1; fi
In file included from fft.c:25:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-file.o -MD -MP -MF ".deps/libffwma_a-file.Tpo" -c -o libffwma_a-file.o `test -f 'file.c' || echo './'`file.c; \
then mv -f ".deps/libffwma_a-file.Tpo" ".deps/libffwma_a-file.Po"; else rm -f ".deps/libffwma_a-file.Tpo"; exit 1; fi
file.c: In function `file_open':
file.c:43: let op: cast to pointer from integer of different size
file.c: In function `file_read':
file.c:49: let op: cast from pointer to integer of different size
file.c: In function `file_write':
file.c:55: let op: cast from pointer to integer of different size
file.c: In function `file_seek':
file.c:62: let op: cast from pointer to integer of different size
file.c: In function `file_close':
file.c:68: let op: cast from pointer to integer of different size
file.c: In function `pipe_open':
file.c:92: let op: cast to pointer from integer of different size
file.c: In function `pipe_read':
file.c:98: let op: cast from pointer to integer of different size
file.c: In function `pipe_write':
file.c:104: let op: cast from pointer to integer of different size
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-futils.o -MD -MP -MF ".deps/libffwma_a-futils.Tpo" -c -o libffwma_a-futils.o `test -f 'futils.c' || echo './'`futils.c; \
then mv -f ".deps/libffwma_a-futils.Tpo" ".deps/libffwma_a-futils.Po"; else rm -f ".deps/libffwma_a-futils.Tpo"; exit 1; fi
futils.c: In function `av_open_input_stream':
futils.c:301: let op: toewijzing maakt pointer van integer zonder een cast
futils.c:315: let op: toewijzing maakt pointer van integer zonder een cast
futils.c: In function `av_find_stream_info':
futils.c:1378: let op: toewijzing maakt pointer van integer zonder een cast
futils.c: In function `av_new_stream':
futils.c:1500: let op: toewijzing maakt pointer van integer zonder een cast
futils.c: In function `av_set_parameters':
futils.c:1524: let op: toewijzing maakt pointer van integer zonder een cast
futils.c: In function `parse_date':
futils.c:1804: let op: toewijzing maakt pointer van integer zonder een cast
futils.c:1825: let op: toewijzing maakt pointer van integer zonder een cast
futils.c:1831: let op: toewijzing maakt pointer van integer zonder een cast
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-mdct.o -MD -MP -MF ".deps/libffwma_a-mdct.Tpo" -c -o libffwma_a-mdct.o `test -f 'mdct.c' || echo './'`mdct.c; \
then mv -f ".deps/libffwma_a-mdct.Tpo" ".deps/libffwma_a-mdct.Po"; else rm -f ".deps/libffwma_a-mdct.Tpo"; exit 1; fi
In file included from mdct.c:19:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-os_support.o -MD -MP -MF ".deps/libffwma_a-os_support.Tpo" -c -o libffwma_a-os_support.o `test -f 'os_support.c' || echo './'`os_support.c; \
then mv -f ".deps/libffwma_a-os_support.Tpo" ".deps/libffwma_a-os_support.Po"; else rm -f ".deps/libffwma_a-os_support.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-parser.o -MD -MP -MF ".deps/libffwma_a-parser.Tpo" -c -o libffwma_a-parser.o `test -f 'parser.c' || echo './'`parser.c; \
then mv -f ".deps/libffwma_a-parser.Tpo" ".deps/libffwma_a-parser.Po"; else rm -f ".deps/libffwma_a-parser.Tpo"; exit 1; fi
parser.c: In function `av_parser_init':
parser.c:44: let op: toewijzing maakt pointer van integer zonder een cast
parser.c:48: let op: toewijzing maakt pointer van integer zonder een cast
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-simple_idct.o -MD -MP -MF ".deps/libffwma_a-simple_idct.Tpo" -c -o libffwma_a-simple_idct.o `test -f 'simple_idct.c' || echo './'`simple_idct.c; \
then mv -f ".deps/libffwma_a-simple_idct.Tpo" ".deps/libffwma_a-simple_idct.Po"; else rm -f ".deps/libffwma_a-simple_idct.Tpo"; exit 1; fi
In file included from simple_idct.c:31:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-utils.o -MD -MP -MF ".deps/libffwma_a-utils.Tpo" -c -o libffwma_a-utils.o `test -f 'utils.c' || echo './'`utils.c; \
then mv -f ".deps/libffwma_a-utils.Tpo" ".deps/libffwma_a-utils.Po"; else rm -f ".deps/libffwma_a-utils.Tpo"; exit 1; fi
In file included from utils.c:24:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
if gcc -DHAVE_CONFIG_H -I. -I. -I../..    -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -g -O2  -MT libffwma_a-wmadec.o -MD -MP -MF ".deps/libffwma_a-wmadec.Tpo" -c -o libffwma_a-wmadec.o `test -f 'wmadec.c' || echo './'`wmadec.c; \
then mv -f ".deps/libffwma_a-wmadec.Tpo" ".deps/libffwma_a-wmadec.Po"; else rm -f ".deps/libffwma_a-wmadec.Tpo"; exit 1; fi
In file included from wmadec.c:26:
dsputil.h:517: let op: static declaration for `lrintf' follows non-static
rm -f libffwma.a
ar cru libffwma.a libffwma_a-allcodecs.o libffwma_a-allformats.o libffwma_a-asf.o libffwma_a-avio.o libffwma_a-aviobuf.o libffwma_a-common.o libffwma_a-cutils.o libffwma_a-dsputil.o libffwma_a-fft.o libffwma_a-file.o libffwma_a-futils.o libffwma_a-mdct.o libffwma_a-os_support.o libffwma_a-parser.o libffwma_a-simple_idct.o libffwma_a-utils.o libffwma_a-wmadec.o
ranlib libffwma.a
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma'
Making all in wma123
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src/wma123'
make[3]: Niets te doen voor `all'.
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src/wma123'
make[3]: Entering directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I./libffwma -L./libffwma -g -O2  -MT bmp-wma.lo -MD -MP -MF ".deps/bmp-wma.Tpo" -c -o bmp-wma.lo bmp-wma.c; \
then mv -f ".deps/bmp-wma.Tpo" ".deps/bmp-wma.Plo"; else rm -f ".deps/bmp-wma.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I./libffwma -L./libffwma -g -O2 -MT bmp-wma.lo -MD -MP -MF .deps/bmp-wma.Tpo -c bmp-wma.c  -fPIC -DPIC -o .libs/bmp-wma.o
bmp-wma.c: In function `get_song_title':
bmp-wma.c:270: warning: assignment discards qualifiers from pointer target type
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I./libffwma -L./libffwma -g -O2 -MT bmp-wma.lo -MD -MP -MF .deps/bmp-wma.Tpo -c bmp-wma.c -o bmp-wma.o >/dev/null 2>&1
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I./libffwma -L./libffwma -g -O2  -MT iir.lo -MD -MP -MF ".deps/iir.Tpo" -c -o iir.lo iir.c; \
then mv -f ".deps/iir.Tpo" ".deps/iir.Plo"; else rm -f ".deps/iir.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I./libffwma -L./libffwma -g -O2 -MT iir.lo -MD -MP -MF .deps/iir.Tpo -c iir.c  -fPIC -DPIC -o .libs/iir.o
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I./libffwma -L./libffwma -g -O2 -MT iir.lo -MD -MP -MF .deps/iir.Tpo -c iir.c -o iir.o >/dev/null 2>&1
/bin/sh ../libtool --mode=link gcc -DXTHREADS -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2   -I./libffwma -L./libffwma -g -O2    -o libwma.la -rpath /usr/lib/bmp/Input -module -avoid-version bmp-wma.lo iir.lo  -lbeep -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lffwma
gcc -shared  .libs/bmp-wma.o .libs/iir.o  -L/usr/lib -L/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma /usr/lib/libbeep.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangoxft-1.0.so /usr/lib/libpangox-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so -lffwma  -Wl,-soname -Wl,libwma.so -o .libs/libwma.so
/usr/bin/ld: /home/twan/Desktop/bmp-wma-0.1.1/src/libffwma/libffwma.a(libffwma_a-allcodecs.o): relocation R_X86_64_32 can not be used when making a shared object; recompile with -fPIC
/home/twan/Desktop/bmp-wma-0.1.1/src/libffwma/libffwma.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libwma.la] Fout 1
make[3]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
make[2]: *** [all-recursive] Fout 1
make[2]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1/src'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/twan/Desktop/bmp-wma-0.1.1'
make: *** [all] Fout 2
```

---

### Post by ablewisuk on 2005-12-06
I had this problem too - to fix it try this:

```
make CC='gcc-3.4 -fpic -DPIC'
```

instead of running make without arguments.

---

