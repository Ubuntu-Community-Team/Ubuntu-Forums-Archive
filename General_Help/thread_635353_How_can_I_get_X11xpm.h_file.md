---
title: "How can I get X11/xpm.h file?"
date: 2007-12-08
forum: General Help
---

### Post by yinglcs2 on 2007-12-08
Can you please tell me how can I get X11/xpm.h file?

I am getting the following compile error "Source/plugin-ui.cpp:6:21: error: X11/xpm.h: No such file or directory". I apreciate if anyone can help. 


g++ -c -o plugin-ui.o -Wall -DXP_UNIX -DMOZ_X11 -I../gecko-sdk -I../gecko-sdk/include -g -O2      -g -O2  -Iinclude -fPIC -DXPCOM_GLUE -DMOZILLA_STRICT_API -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  Source/plugin-ui.cpp
Source/plugin-ui.cpp:6:21: error: X11/xpm.h: No such file or directory

---

### Post by Portable_Jim on 2007-12-10
You could try installing libxpm-dev ```
sudo aptitude install libxpm-dev
```

---

