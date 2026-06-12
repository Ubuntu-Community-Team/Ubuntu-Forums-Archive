---
title: "cheese make problem"
date: 2013-04-10
forum: General Help
---

### Post by ac98521 on 2013-04-10
so I downloaded cheese 3.8 tar.xz and left it in the downloads folder and I went to the extracted folder of cheese and ran** ./configure**
[B]
EDIT

[/B]it said I have to install Intltool [http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html) so I did and when I did it said I don't have gudev.

I installed gudev then when I tried ./configure again here is what happened at my face

configure: error: Package requirements (glib-2.0 >= 2.28.0
  gio-2.0 >= 2.28.0
  x11
  gobject-2.0 >= 2.28.0
  gdk-pixbuf-2.0
  gstreamer-plugins-base-1.0 >= 0.11.0 gstreamer-1.0 >= 0.11.0 gstreamer-pbutils-1.0 >= 0.11.0
  gstreamer-plugins-bad-1.0 >= 0.11.0
  cairo >= 1.10.0
  pangocairo >= 1.28.0
  clutter-1.0 >= 1.10.0
  clutter-gst-2.0 >= 1.9.0
  gudev-1.0) were not met:


No package 'x11' found
No package 'gdk-pixbuf-2.0' found
No package 'gstreamer-plugins-base-1.0' found
No package 'gstreamer-1.0' found
No package 'gstreamer-pbutils-1.0' found
No package 'gstreamer-plugins-bad-1.0' found
No package 'cairo' found
No package 'pangocairo' found
No package 'clutter-1.0' found
No package 'clutter-gst-2.0' found


Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
brian@brian-K40IJ:~/Downloads/cheese-3.8.0$ ^C
brian@brian-K40IJ:~/Downloads/cheese-3.8.0$ make
make: *** No targets specified and no makefile found.  Stop.



&#8203;so what is this now?

I can't proceed with make

---

### Post by davidvandoren on 2013-04-10
First of all, why do you need to install cheese from source?

Is there anything special about the 3.8 version?

IF not, open the ubuntu software center and search for cheese, click on install, enter your admin password, that's it.

Or install GUVCVIEW. It is in the software center also.

Or open you rterminal and type
```
sudo apt-get install cheese
```

```
sudo apt-get install guvcview
```

If you really need to install cheese 3.8 from source, my best guess is that you need all the essentials for building from source. You can go here and hav ea look, but no gurantee! [http://forums.linuxmint.com/viewtopic.php?f=90&t=118811](http://forums.linuxmint.com/viewtopic.php?f=90&t=118811)
```
sudo apt-get install build-essential gdk-pixbuf2.0-dev libghc-gstreamer-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev libcairo-dev libghc-pango-dev libclutter-1.0-dev libclutter-gst-dev libclutter-gst-2.0-dev libclutter-gtk-1.0-dev libcheese-dev libcheese-gtk-dev libgnome-desktop-3-dev libgee-devlibrsvg2-dev gnome-video-effects-dev itstool
```.

---

### Post by ac98521 on 2013-04-10
actually that was the guide I used but. didn't work because of the error that appeared in front of me o.O

When I ran the code
Note, selecting 'libgdk-pixbuf2.0-dev' for regex 'gdk-pixbuf2.0-dev'
Note, selecting 'libcairo2-dev' instead of 'libcairo-dev'
E: Unable to locate package libgstreamer-plugins-base1.0-dev
E: Couldn't find any package by regex 'libgstreamer-plugins-base1.0-dev'
E: Unable to locate package libgstreamer-plugins-bad1.0-dev
E: Couldn't find any package by regex 'libgstreamer-plugins-bad1.0-dev'
E: Unable to locate package libclutter-gst-2.0-dev
E: Couldn't find any package by regex 'libclutter-gst-2.0-dev'
E: Unable to locate package libgee-devlibrsvg2-dev

---

### Post by oldos2er on 2013-04-11
Try ```
sudo apt-get build-dep cheese
```

---

