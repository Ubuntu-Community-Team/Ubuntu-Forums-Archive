---
title: "Can glade-3.18.3 and gtk+-3.12.2 etc. be installed on Ubuntu 12.04?"
date: 2014-08-26
forum: General Help
---

### Post by dragonfly41 on 2014-08-26
Can glade-3.18.3 and gtk+-3.12.2 etc. be installed on Ubuntu 12.04 .. or does it need Ubuntu 14.04?

Not sure whether to post here or in Programming sub-forum.

I have Ubuntu 12.04 and I'm not sure if I can install glade-3.18.3 and gtk+-3.12.2 which so far I've downloaded.  
Glade-3.18.3 has a number of dependencies not found in Ubuntu 12.04 Software Centre.

I start running ./configure  in gtk+-3.12.2 directory and I get this far ...

```
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.39.5    atk >= 2.7.5    pango >= 1.32.4    cairo >= 1.12.0    cairo-gobject >= 1.12.0    gdk-pixbuf-2.0 >= 2.27.1) were not met:

Requested 'glib-2.0 >= 2.39.5' but version of GLib is 2.32.4
Requested 'atk >= 2.7.5' but version of Atk is 2.4.0
Requested 'pango >= 1.32.4' but version of Pango is 1.30.0
Requested 'cairo >= 1.12.0' but version of cairo is 1.10.2
Requested 'cairo-gobject >= 1.12.0' but version of cairo-gobject is 1.10.2
Requested 'gdk-pixbuf-2.0 >= 2.27.1' but version of GdkPixbuf is 2.26.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```


Can I manually install these dependencies on Ubuntu 12.04 or do I now need to consider a move to Ubuntu 14.04 (which so far I've avoided)?

---

