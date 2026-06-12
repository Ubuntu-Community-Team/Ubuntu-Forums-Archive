---
title: "Installing Pidgin on Ubuntu 7.4"
date: 2007-08-20
forum: General Help
---

### Post by saby4237 on 2007-08-20
**Sought to install Pidgin by the following method:**

Howto : Compile Pidgin 2.1.0 on Ubuntu 7.04
Pidgin (formerly known as Gaim) is arguably the best IM client currently available. Capable of chatting on more than 15 different protocols including MSN, IRC and AIM. But so far it has not been added to the Ubuntu 7.04 repositories. This post will guide you through compiling Pidgin 2.1.0 on Ubuntu 7.04.

Step 1 - Getting the Source code
There is no official Pidgin deb files, released from Ubuntu or Pidgin so the best way to install it is to compile it from source. To do this we must first have the source code extracted on our hard drive.
Go to [www.pidgin.im](www.pidgin.im) and download the latest source tar.bz2 (At time of writing the latest version is 2.1.0). Once it has finished downloading extract it into your home directory.

Step 2 - Dependencies
As the source code doesn’t come with all the dependencies required for it to run we have to download them ourselves. Luckily Ubuntu has all of the dependencies required in their repositories so we don’t have too much compiling to do.

To get all the dependencies run:
sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev libgtkspell-dev libnss-dev libnspr-dev build-essential

Step 3 - Compiling
 Next do ‘cd pidgin-X.X.X’, ‘./configure’, ‘make’, ‘make install’.
And now you can run Pidgin by ‘pidgin’. I also added Pidgin to my Gnome Panel. The command to run is ‘/usr/local/bin/pidgin’.
[N.B.: X.X.X = Version No.]

However, near the end I'm getting the error message as shown in the attachment to this message.

Please help....

---

### Post by Ek0nomik on 2007-08-20
Can you please post the error message in a reply to this thread?  Just copy and paste all of your terminal output and paste it in a code (#) box.

Or if you post an image make it big enough so I can read it.  It's pretty small.  :)

Cheers!

---

### Post by kostkon on 2007-08-20
Why don't you get the [deb file for *Pidgin* from *getdeb.net*]("http://www.getdeb.net/release.php?id=1209") and install it easily? You don't need to compile it.

---

### Post by Ek0nomik on 2007-08-20
> **kostkon said:**
> Why don't you get the [deb file for *Pidgin* from *getdeb.net*]("http://www.getdeb.net/release.php?id=1209") and install it easily? You don't need to compile it.

Perhaps he wanted to compile it himself?

---

### Post by saby4237 on 2007-08-20
> **Ek0nomik said:**
> Perhaps he wanted to compile it himself?

I'm sorry, I'm a mere user and have no technical knowledge whatsoever. I'm copying my terminal message in to to:

make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/32/scalable'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/32/scalable'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/32'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/32'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/32'
Making all in 48
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48'
Making all in rtl
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48/rtl'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48/rtl'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status/48'
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status'
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/status'
Making all in toolbar
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar'
Making all in 16
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16'
Making all in scalable
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16/scalable'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16/scalable'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/16'
Making all in 22
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22'
Making all in scalable
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22/scalable'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22/scalable'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar/22'
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar'
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/toolbar'
Making all in tray
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray'
Making all in 16
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16'
Making all in scalable
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16/scalable'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16/scalable'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/16'
Making all in 22
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22'
Making all in scalable
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22/scalable'
make[6]: Nothing to be done for `all'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22/scalable'
make[6]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22'
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/22'
Making all in 32
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/32'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/32'
Making all in 48
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/48'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray/48'
make[5]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray'
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps/tray'
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/pixmaps'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps'
make[3]: Leaving directory `/home/sabyasachi/pidgin/pidgin/pixmaps'
Making all in plugins
make[3]: Entering directory `/home/sabyasachi/pidgin/pidgin/plugins'
Making all in gestures
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/plugins/gestures'
if /bin/bash ../../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../..  -DDATADIR=\"/usr/local/share\" -I../../../libpurple -I../../../libpurple -I../../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -g -g -O2 -MT gestures.lo -MD -MP -MF ".deps/gestures.Tpo" -c -o gestures.lo gestures.c; \
        then mv -f ".deps/gestures.Tpo" ".deps/gestures.Plo"; else rm -f ".deps/gestures.Tpo"; exit 1; fi
/bin/bash ../../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o gestures.la -rpath /usr/local/lib/pidgin -module -avoid-version gestures.lo stroke.lo stroke-draw.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/plugins/gestures'
Making all in ticker
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/plugins/ticker'
if /bin/bash ../../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../..  -DDATADIR=\"/usr/local/share\" -I../../../libpurple -I../../../libpurple -I../../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12     -g -g -O2 -MT ticker.lo -MD -MP -MF ".deps/ticker.Tpo" -c -o ticker.lo ticker.c; \
        then mv -f ".deps/ticker.Tpo" ".deps/ticker.Plo"; else rm -f ".deps/ticker.Tpo"; exit 1; fi
/bin/bash ../../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o ticker.la -rpath /usr/local/lib/pidgin -module -avoid-version gtkticker.lo ticker.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/plugins/ticker'
make[4]: Entering directory `/home/sabyasachi/pidgin/pidgin/plugins'
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT contact_priority.lo -MD -MP -MF ".deps/contact_priority.Tpo" -c -o contact_priority.lo contact_priority.c; \
        then mv -f ".deps/contact_priority.Tpo" ".deps/contact_priority.Plo"; else rm -f ".deps/contact_priority.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o contact_priority.la  -module -avoid-version contact_priority.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT gtk-signals-test.lo -MD -MP -MF ".deps/gtk-signals-test.Tpo" -c -o gtk-signals-test.lo gtk-signals-test.c; \
        then mv -f ".deps/gtk-signals-test.Tpo" ".deps/gtk-signals-test.Plo"; else rm -f ".deps/gtk-signals-test.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o gtk_signals_test.la  -module -avoid-version gtk-signals-test.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT convcolors.lo -MD -MP -MF ".deps/convcolors.Tpo" -c -o convcolors.lo convcolors.c; \
        then mv -f ".deps/convcolors.Tpo" ".deps/convcolors.Plo"; else rm -f ".deps/convcolors.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o convcolors.la -rpath /usr/local/lib/pidgin -module -avoid-version convcolors.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT extplacement.lo -MD -MP -MF ".deps/extplacement.Tpo" -c -o extplacement.lo extplacement.c; \
        then mv -f ".deps/extplacement.Tpo" ".deps/extplacement.Plo"; else rm -f ".deps/extplacement.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o extplacement.la -rpath /usr/local/lib/pidgin -module -avoid-version extplacement.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT gtkbuddynote.lo -MD -MP -MF ".deps/gtkbuddynote.Tpo" -c -o gtkbuddynote.lo gtkbuddynote.c; \
        then mv -f ".deps/gtkbuddynote.Tpo" ".deps/gtkbuddynote.Plo"; else rm -f ".deps/gtkbuddynote.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o gtkbuddynote.la -rpath /usr/local/lib/pidgin -module -avoid-version gtkbuddynote.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT history.lo -MD -MP -MF ".deps/history.Tpo" -c -o history.lo history.c; \
        then mv -f ".deps/history.Tpo" ".deps/history.Plo"; else rm -f ".deps/history.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o history.la -rpath /usr/local/lib/pidgin -module -avoid-version history.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT iconaway.lo -MD -MP -MF ".deps/iconaway.Tpo" -c -o iconaway.lo iconaway.c; \
        then mv -f ".deps/iconaway.Tpo" ".deps/iconaway.Plo"; else rm -f ".deps/iconaway.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o iconaway.la -rpath /usr/local/lib/pidgin -module -avoid-version iconaway.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT markerline.lo -MD -MP -MF ".deps/markerline.Tpo" -c -o markerline.lo markerline.c; \
        then mv -f ".deps/markerline.Tpo" ".deps/markerline.Plo"; else rm -f ".deps/markerline.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o markerline.la -rpath /usr/local/lib/pidgin -module -avoid-version markerline.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT notify.lo -MD -MP -MF ".deps/notify.Tpo" -c -o notify.lo notify.c; \
        then mv -f ".deps/notify.Tpo" ".deps/notify.Plo"; else rm -f ".deps/notify.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o notify.la -rpath /usr/local/lib/pidgin -module -avoid-version notify.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT pidginrc.lo -MD -MP -MF ".deps/pidginrc.Tpo" -c -o pidginrc.lo pidginrc.c; \
        then mv -f ".deps/pidginrc.Tpo" ".deps/pidginrc.Plo"; else rm -f ".deps/pidginrc.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o pidginrc.la -rpath /usr/local/lib/pidgin -module -avoid-version pidginrc.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT relnot.lo -MD -MP -MF ".deps/relnot.Tpo" -c -o relnot.lo relnot.c; \
        then mv -f ".deps/relnot.Tpo" ".deps/relnot.Plo"; else rm -f ".deps/relnot.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o relnot.la -rpath /usr/local/lib/pidgin -module -avoid-version relnot.lo -Wl,--export-dynamic -pthread -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lrt -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT spellchk.lo -MD -MP -MF ".deps/spellchk.Tpo" -c -o spellchk.lo spellchk.c; \
        then mv -f ".deps/spellchk.Tpo" ".deps/spellchk.Plo"; else rm -f ".deps/spellchk.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o spellchk.la -rpath /usr/local/lib/pidgin -module -avoid-version spellchk.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT timestamp.lo -MD -MP -MF ".deps/timestamp.Tpo" -c -o timestamp.lo timestamp.c; \
        then mv -f ".deps/timestamp.Tpo" ".deps/timestamp.Plo"; else rm -f ".deps/timestamp.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o timestamp.la -rpath /usr/local/lib/pidgin -module -avoid-version timestamp.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT timestamp_format.lo -MD -MP -MF ".deps/timestamp_format.Tpo" -c -o timestamp_format.lo timestamp_format.c; \
        then mv -f ".deps/timestamp_format.Tpo" ".deps/timestamp_format.Plo"; else rm -f ".deps/timestamp_format.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o timestamp_format.la -rpath /usr/local/lib/pidgin -module -avoid-version timestamp_format.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
if /bin/bash ../../libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..  -DDATADIR=\"/usr/local/share\" -I../../libpurple -I../../libpurple -I../../pidgin -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -g -O2 -MT xmppconsole.lo -MD -MP -MF ".deps/xmppconsole.Tpo" -c -o xmppconsole.lo xmppconsole.c; \
        then mv -f ".deps/xmppconsole.Tpo" ".deps/xmppconsole.Plo"; else rm -f ".deps/xmppconsole.Tpo"; exit 1; fi
/bin/bash ../../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o xmppconsole.la -rpath /usr/local/lib/pidgin -module -avoid-version xmppconsole.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -lnsl -lresolv 
make[4]: Leaving directory `/home/sabyasachi/pidgin/pidgin/plugins'
make[3]: Leaving directory `/home/sabyasachi/pidgin/pidgin/plugins'
Making all in sounds
make[3]: Entering directory `/home/sabyasachi/pidgin/pidgin/sounds'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sabyasachi/pidgin/pidgin/sounds'
make[3]: Entering directory `/home/sabyasachi/pidgin/pidgin'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -DBR_PTHREADS=0 -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib/pidgin/\" -DLOCALEDIR=\"/usr/local/share/locale\" -DSYSCONFDIR=\"/usr/local/etc\" -I../libpurple -I../libpurple/ -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wall  -Waggregate-return -Wcast-align -Wdeclaration-after-statement -Wendif-labels -Werror-implicit-function-declaration -Wextra -Wno-sign-compare -Wno-unused-parameter -Winit-self -Wmissing-declarations -Wmissing-noreturn -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wundef -Wp,-D_FORTIFY_SOURCE=2 -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -DPNG_NO_MMX_CODE -I/usr/include/gtkspell-2.0 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12    -I/usr/include/libxml2   -DUSE_INTERNAL_LIBGADU   -g -g -O2 -MT gtkconv.o -MD -MP -MF ".deps/gtkconv.Tpo" -c -o gtkconv.o gtkconv.c; \
        then mv -f ".deps/gtkconv.Tpo" ".deps/gtkconv.Po"; else rm -f ".deps/gtkconv.Tpo"; exit 1; fi
/bin/bash ../libtool --silent --tag=CC --mode=link gcc  -g -g -O2   -o pidgin -export-dynamic eggtrayicon.o pidgincombobox.o pidginstock.o gtkaccount.o gtkblist.o gtkcelllayout.o gtkcellrendererexpander.o gtkcellrendererprogress.o gtkcellview.o gtkcellviewmenuitem.o gtkconn.o gtkconv.o gtkdebug.o gtkdialogs.o gtkdnd-hints.o gtkdocklet.o gtkdocklet-x11.o gtkeventloop.o gtkexpander.o gtkft.o gtkidle.o gtkimhtml.o gtkimhtmltoolbar.o gtklog.o gtkmain.o gtkmenutray.o gtknotify.o gtkplugin.o gtkpluginpref.o gtkpounce.o gtkprefs.o gtkprivacy.o gtkrequest.o gtkroomlist.o gtksavedstatuses.o gtkscrollbook.o gtksession.o gtksound.o gtksourceiter.o gtksourceundomanager.o gtksourceview-marshal.o gtkstatusbox.o gtkthemes.o gtkutils.o gtkwhiteboard.o    -lSM -lICE  -lgtkspell -laspell -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    -lxml2   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   ../libpurple/libpurple.la -lnsl -lresolv 
make[3]: Leaving directory `/home/sabyasachi/pidgin/pidgin'
make[2]: Leaving directory `/home/sabyasachi/pidgin/pidgin'
Making all in m4macros
make[2]: Entering directory `/home/sabyasachi/pidgin/m4macros'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sabyasachi/pidgin/m4macros'
Making all in po
make[2]: Entering directory `/home/sabyasachi/pidgin/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sabyasachi/pidgin/po'
make[2]: Entering directory `/home/sabyasachi/pidgin'
make[2]: Leaving directory `/home/sabyasachi/pidgin'
make[1]: Leaving directory `/home/sabyasachi/pidgin'
sabyasachi@sabyasachi-desktop:~/pidgin$ 
sabyasachi@sabyasachi-desktop:~/pidgin$ pidgin
bash: pidgin: command not found
sabyasachi@sabyasachi-desktop:~/pidgin$ make install
Making install in libpurple
make[1]: Entering directory `/home/sabyasachi/pidgin/libpurple'
make  install-recursive
make[2]: Entering directory `/home/sabyasachi/pidgin/libpurple'
Making install in gconf
make[3]: Entering directory `/home/sabyasachi/pidgin/libpurple/gconf'
make[4]: Entering directory `/home/sabyasachi/pidgin/libpurple/gconf'
make[4]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule purple.schemas 2>&1 | \
                grep -v "^WARNING: failed to install schema" | grep -v "^Attached schema" 1>&2
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
None of the resolved addresses are writable; saving configuration settings will not be possible
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
mkdir: cannot create directory `/usr/local/etc/gconf': Permission denied
make[4]: *** [install-schemaDATA] Error 1
make[4]: Leaving directory `/home/sabyasachi/pidgin/libpurple/gconf'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/sabyasachi/pidgin/libpurple/gconf'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/sabyasachi/pidgin/libpurple'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/sabyasachi/pidgin/libpurple'
make: *** [install-recursive] Error 1
sabyasachi@sabyasachi-desktop:~/pidgin$ 


The errors in the last part seem to be the hitch. Please help me out when you have the time.
 And I had downloaded the .tar file from the link given above. Yet the above errors occured. Must be due to some fault on my part. But I don't have the know-how to understand what fault!
Thanks in advance.

---

### Post by UI-Freak on 2007-08-21
Get the installer here and save tons of time and tears:

[http://www.getdeb.net/release.php?id=1209](http://www.getdeb.net/release.php?id=1209)

---

### Post by saby4237 on 2007-08-21
I'd request some guidance please. I'm downloading the two files, pidgin and pidgin-data from the link given by you. 
What should I do after that? Use Synaptic Package Manager or just type 'sudo apt-get install and then the 'pidgin' pack or what? Sorry, but I'm a layman and will require some step-by-step assistance!

---

### Post by kostkon on 2007-08-21
Just double click on *pidgin-data.deb* file first, and a window will open that will allow you to install it. You should be able to do it easily. Then do the same thing for the *pidgin.deb* file.

---

### Post by Depressed Man on 2007-08-21
saby4237, just for future reference (it makes it easier to navigate forums ;) ). There are code tags. 

[CODE*]code, terminal output, whatever can go in here[/*CODE]

Take out the * of course (for it to work). That way when its posted it'll be in a self contained scrollable box and won't make the post so long :).

---

### Post by saby4237 on 2007-08-21
I have no words sufficient to thank you people. 
Pidgin installed smoothly. I missed out simple steps and was trying to install Pidgin the hard way via the command line by reading instructions from some site.
 Anyway, I'll disturb you one last time.
 I want to install Google Talk via Pidgin. Should I follow the instructions in this link? :
[http://www.google.com/support/a/bin/answer.py?answer=49147](http://www.google.com/support/a/bin/answer.py?answer=49147)

---

### Post by saby4237 on 2007-08-21
Wow, got Google Talk and Yahoo Messenger configured. Thanks again buddies!:lolflag:

---

