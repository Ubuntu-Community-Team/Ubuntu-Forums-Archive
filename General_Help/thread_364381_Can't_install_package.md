---
title: "Can't install package"
date: 2007-02-18
forum: General Help
---

### Post by Nirva on 2007-02-18
Hi,

I am trying to install gset-compiz, but when I make this source there is an error that has something to do with libGTK2.0.
So I went to the Synaptic Packages Manager and tried installing the package : "libgtk+2.0-directfb0 ".  
When I mark it for installation, I get an error :
 "libgtk+2.0-directfb0:  Depends: libdirectfb-0.9-22  but it is not installable".
Does someone knows how I should solve this?
Has it something to do with my repos?

Thanks

---

### Post by xopher on 2007-02-18
As far as I know you shouldn't be installing that either. It's awfully outdated/depricated software.

What guide were you following?

---

### Post by Nirva on 2007-02-18
I'm not really following any guide, I just downloaded this file : 
[http://sonique54.free.fr/xgl/rpms/gset-compiz-0.3.3.tar.gz](http://sonique54.free.fr/xgl/rpms/gset-compiz-0.3.3.tar.gz)
I configured it and tried making it, but I got this error : 


[I]
[email]filip@Filip:~/Desktop/gset-compiz-0.3.3.tar.gz[/email]_FILES$ make
make  all-recursive
make[1]: Entering directory `/home/filip/Desktop/gset-compiz-0.3.3.tar.gz_FILES'
Making all in src
make[2]: Entering directory `/home/filip/Desktop/gset-compiz-0.3.3.tar.gz_FILES/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0   -pthread -DORBIT2=1 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0   -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0     -DDATADIR=\"/usr/share/gset-compiz\" -DPIXDIR=\"/usr/share/pixmaps\" -export-dynamic -g -O2 -MT gset.o -MD -MP -MF ".deps/gset.Tpo" -c -o gset.o gset.c; \
        then mv -f ".deps/gset.Tpo" ".deps/gset.Po"; else rm -f ".deps/gset.Tpo"; exit 1; fi
In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkbin.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkwindow.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkdialog.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkaboutdialog.h:28,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from gset.c:1:
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before ‘GInitiallyUnowned’
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before ‘GInitiallyUnownedClass’
make[2]: *** [gset.o] Error 1
make[2]: Leaving directory `/home/filip/Desktop/gset-compiz-0.3.3.tar.gz_FILES/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/filip/Desktop/gset-compiz-0.3.3.tar.gz_FILES'
make: *** [all] Error 2
[email]filip@Filip:~/Desktop/gset-compiz-0.3.3.tar.gz[/email]_FILES$ 
[/I]

---

