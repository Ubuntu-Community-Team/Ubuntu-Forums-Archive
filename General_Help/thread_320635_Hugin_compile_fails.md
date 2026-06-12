---
title: "Hugin compile fails"
date: 2006-12-17
forum: General Help
---

### Post by hareti on 2006-12-17
Hi there, I'm still having some trouble compiling Hugin. I've installed all the required libraries like libpano and enblend but the compile fails with the following errors :

```
make[4]: wxrc: Command not found
make[4]: [vig_corr_dlg.xrs] Error 127 (ignored)
touch stamp-xrs
make[4]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin/xrc'
make[3]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin/xrc'
Making all in po
make[3]: Entering directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin/po'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin/po'
make[3]: Entering directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin'
if g++ -DHAVE_CONFIG_H "-I." -I../../src/include -I../../src/foreign -I../../src/include -I.. -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D_LARGEFILE_SOURCE=1 -DNO_GCC_PRAGMA    -I/usr/local/include -DHasPANO -pthread -I/usr/include -DINSTALL_XRC_DIR=\"/usr/local/share/hugin/xrc\" -DINSTALL_LOCALE_DIR=\"/usr/local/share/locale\" -g -O2 -MT UniversalCursor.o -MD -MP -MF ".deps/UniversalCursor.Tpo" \
          -c -o UniversalCursor.o `test -f 'UniversalCursor.cpp' || echo './'`UniversalCursor.cpp; \
        then mv -f ".deps/UniversalCursor.Tpo" ".deps/UniversalCursor.Po"; \
        else rm -f ".deps/UniversalCursor.Tpo"; exit 1; \
        fi
UniversalCursor.cpp:68:21: error: gdk/gdk.h: No such file or directory
UniversalCursor.cpp:69:21: error: gtk/gtk.h: No such file or directory
UniversalCursor.cpp: In constructor \u2018UniversalCursor::UniversalCursor(const wxImage&)\u2019:
UniversalCursor.cpp:224: error: invalid use of undefined type \u2018struct _GtkWidget\u2019
/usr/include/wx-2.6/wx/defs.h:2703: error: forward declaration of \u2018struct _GtkWidget\u2019
UniversalCursor.cpp:225: error: \u2018gdk_bitmap_create_from_data\u2019 was not declared in this scope
UniversalCursor.cpp:226: error: invalid use of undefined type \u2018struct _GtkWidget\u2019
/usr/include/wx-2.6/wx/defs.h:2703: error: forward declaration of \u2018struct _GtkWidget\u2019
UniversalCursor.cpp:237: error: \u2018gdk_cursor_new_from_pixmap\u2019 was not declared in this scope
UniversalCursor.cpp:239: error: \u2018gdk_bitmap_unref\u2019 was not declared in this scope
make[3]: *** [UniversalCursor.o] Error 1
make[3]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src/hugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gareth/install/Linux/hugin-0.6.1/src'
make: *** [all-recursive] Error 1
```


For some reason it can't find gtk.h and gdk.h. I definitely have the development libraries for GTK installed and the files that it can't find are there :

```
/usr/include/gtk-1.2/gtk/gtk.h
/usr/include/gtk-2.0/gtk/gtk.h
/usr/include/gtk-1.2/gtk/gdk.h
/usr/include/gtk-2.0/gtk/gdk.h
```

The packages I have installed are :

```
libgtk1.2
libgtk1.2-common
libgtk1.2-dev
```

as well as the 2.0 versions of these.

Are there some other packages I still need for it to work?

Thanks

---

### Post by hareti on 2006-12-17
Thinking about it now I've compiled other software that uses GTK so could it be problem with the source itself?

---

