---
title: "trying to install noisee generator plugin for gimp and i'm getting this..."
date: 2013-05-07
forum: General Help
---

### Post by am_i_registered on 2013-05-07
hi,
i'm trying to install the [noise generator plugin]("http://registry.gimp.org/node/13016") for GIMP 2.8.4 and when i'm typing 

```
make
```

i'm getting this:

```
make -C po
make[1]: Entering directory `/home/am_i_registered/Downloads/noise-generator-0.2.5/po'
msgfmt -c -v -o de.mo de.po
34 translated messages.
msgfmt -c -v -o pl.mo pl.po
34 translated messages.
make[1]: Leaving directory `/home/am_i_registered/Downloads/noise-generator-0.2.5/po'
make -C src
make[1]: Entering directory `/home/am_i_registered/Downloads/noise-generator-0.2.5/src'
cc -O3 -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/harfbuzz -I/usr/include/gimp-2.0   -o noise-generator plugin.o noise.o events.o interface.o colour.o poisson_gui.o gauss_gui.o uniform_gui.o laplace_gui.o lorentz_gui.o -lgimpui-2.0 -lgimpwidgets-2.0 -lgimpmodule-2.0 -lgimp-2.0 -lgimpmath-2.0 -lgimpconfig-2.0 -lgimpcolor-2.0 -lgimpbase-2.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lglib-2.0  
/usr/bin/ld: events.o: undefined reference to symbol 'floor@@GLIBC_2.2.5'
/usr/bin/ld: note: 'floor@@GLIBC_2.2.5' is defined in DSO /lib/x86_64-linux-gnu/libm.so.6 so try adding it to the linker command line
/lib/x86_64-linux-gnu/libm.so.6: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[1]: *** [noise-generator] Error 1
make[1]: Leaving directory `/home/am_i_registered/Downloads/noise-generator-0.2.5/src'
make: *** [src] Error 2

```

i don't really understand what's going on... so please help me if you can!
thanks

---

### Post by Feliks on 2013-10-27
The same over here. With Gimp 2.6 it worked perfectly, with Gimp 2.8 same result as yours

---

