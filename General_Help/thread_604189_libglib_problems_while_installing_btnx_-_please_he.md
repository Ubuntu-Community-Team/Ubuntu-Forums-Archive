---
title: "libglib problems while installing btnx - please help!"
date: 2007-11-05
forum: General Help
---

### Post by kdx on 2007-11-05
I'm trying to install btnx for my Logitech VX Revolution mouse using [this]("http://ubuntuforums.org/showthread.php?t=455656") tutorial.

However, when run ./configure while attempting to install the btnx-config portion of the program, I get this error: 

> checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.12.11) were not met:

Requested 'glib-2.0 >= 2.12.11' but version of GLib is 2.0.7

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I looked in Synaptic to check my version of libglib, and it says that I have version 2.12.11-0ubuntu1.  I'm assuming that this is the same as 2.12.11.  

I've also installed the -dbg, -cil, -data, and -dev versions as well, hoping to resolve this issue, but to no avail.

So, if I have the right version installed, why is there an issue? :confused:

I've already attempted to reinstall libglib, as well as download the tar.gz again.  

Thanks for your help!

---

### Post by kdx on 2007-11-06
Nevermind, I fixed it.  It seems that there were some symlinks hidden in my system.  I placed them into  another folder, just in case they ended up being important later.  With them out of the way, the program compiled just fine!

---

