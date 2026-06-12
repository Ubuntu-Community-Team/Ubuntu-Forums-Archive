---
title: "installing gdk-pixbuf"
date: 2007-07-06
forum: General Help
---

### Post by deadpickle on 2007-07-06
When I try to configure libral 0.61 in Ubuntu 7.04 I get the error:
[B]
checking for GDK_PIXBUF... configure: error: Package requirements (gdk-pixbuf-2.0) were not met:

No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_PIXBUF_CFLAGS
and GDK_PIXBUF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

So I downloaded gdk-pixbuf 0.22 and tried to install it. Configure seemed to work but when I ran make I got the error:

[B]make[3]: *** [gdk-pixbuf-xlib.lo] Error 1
make[3]: Leaving directory `/home/deadpickle/Desktop/gdk-pixbuf-0.22.0/gdk-pixbuf'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/deadpickle/Desktop/gdk-pixbuf-0.22.0/gdk-pixbuf'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/deadpickle/Desktop/gdk-pixbuf-0.22.0'
make: *** [all-recursive-am] Error 2
[/B]
I'm not sure what this means but I could use some help. Any ideas?

---

### Post by danielmendesleao on 2007-07-19
where did you download it ?? i'm also looking for it over the web...

---

