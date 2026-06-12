---
title: "weird compile error"
date: 2007-05-14
forum: General Help
---

### Post by orrorin on 2007-05-14
While compiling vim for GUI from source, I get the following error ...

gcc -c -I. -Iproto -DHAVE_CONFIG_H -DFEAT_GUI_GTK  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/libpng12 -I/usr/include/libxml2     -O2 -fno-strength-reduce -Wall         -o objects/gui_gtk.o gui_gtk.c
In file included from /usr/include/glib-2.0/glib/gi18n.h:23,
                 from /usr/include/libbonobo-2.0/bonobo/bonobo-i18n.h:37,
                 from /usr/include/libgnome-2.0/libgnome/gnome-i18n.h:41,
                 from /usr/include/libgnome-2.0/libgnome/libgnome.h:30,
                 from /usr/include/libgnomeui-2.0/gnome.h:5,
                 from gui_gtk.c:62:
/usr/include/libintl.h:92: error: expected identifier or ‘(’ before ‘;’ token
make[2]: *** [objects/gui_gtk.o] Error 1
make[2]: Leaving directory `/home/tushar/vim/vim71/src'
make[1]: *** [myself] Error 2
make[1]: Leaving directory `/home/tushar/vim/vim71/src'
make: *** [first] Error 2
aristotle:~/vim/vim71> 


Any ideas on this?I installed feisty earlier today.

---

