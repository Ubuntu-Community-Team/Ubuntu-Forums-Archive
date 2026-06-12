---
title: "Autoclick"
date: 2019-07-26
forum: General Help
---

### Post by nathanlesko on 2019-07-26
Can anyone help me install xAutoclick[ https://sourceforge.net/projects/xautoclick/]("https://sourceforge.net/projects/xautoclick/")

in Xubuntu/Ubuntu 18.04? I had it installed in Xubuntu 16.04. It looks like the project is not supported anymore, but this was a great little program to auto click the mouse at specified intervals. It compiles successfully but make fails with:

 Makefile:96: recipe for target 'all' failed
make: *** [all] Error 2

I'm not real proficient in Linux yet, and any help would be greatly appreciated.

---

### Post by wildmanne39 on 2019-07-26
Hello, the link you added does not work.

---

### Post by Holger_Gehrke on 2019-07-27
A quick search on sourceforge gave me [this]("https://sourceforge.net/projects/xautoclick/").
You need to run the 'configure' script before running 'make' because it creates or configures the Makefile for your system. It checks for the availability of needed tools and libraries. You'll need make, compilers for C and C++, and the development packages for the libraries used by the program. If all of these are available, configure will create the Makefile and you can compile the program.

Holger

---

### Post by nathanlesko on 2019-07-27
Here's my confgure output: Make command still giving me errors

Checking for c compiler ... gcc
Checking for c++ compiler ... g++
Checking for GNU Make ... yes, using make
Checking for extra headers ... no
Checking for extra libraries ... no
Checking for gcc support of -MM option ... yes
Checking for g++ support of -MM option ... yes
Checking for inttypes.h ... yes
Checking for unistd.h ... yes
Checking for malloc.h ... yes
Checking for X11 header presence ... yes (using /usr/include)
Checking for X11 ... yes (using -L/usr/lib -lX11 -lXext)
Checking for XTest extension ... yes
Checking for gtk-config ... no
Not building gAutoClick
Checking for pkg-config ... pkg-config
Checking for GTK+ 2.0 ... yes
Checking for GTK+ 2.0 cflags ... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16
Checking for GTK+ 2.0 libs ... -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangocairo-1.0 -latk-1.0 -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0 -lfontconfig -lfreetype
Checking for glib 2.0 cflags ... -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include
Checking for glib 2.0 libs ... -lglib-2.0
Checking for Qt 3 ... no
Checking for Qt 4 ... yes
Checking for Qt 4 cflags ... -DQT_SHARED -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I/usr/include/qt4/QtCore
Checking for Qt 4 libs ... -lQtGui -lQtCore
Checking for fltk-config ... fltk-config
Checking for FLTK ... yes
Checking for FLTK cflags ... -I/usr/include/cairo -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 
Checking for FLTK libs ... -lfltk -lX11

Debug symbols disabled.
All compiler warnings disabled.

Cleaning up source tree ... done

Generating config.mak ... done.

aAutoClick    : yes
cAutoClick    : yes
gAutoClick    : no
gAutoClick2   : yes
qtAutoClick   : no
qt4AutoClick  : yes
fltkAutoClick : yes

Installation prefix : /usr/local

Now type 'make' to build.

---

