---
title: "Can't get my scanner to work... Please help!"
date: 2008-03-07
forum: General Help
---

### Post by rift400 on 2008-03-07
Hi
I've got an epson RX630 and I'm trying to install the drivers for it (not supported in standard SANE list as far as I can tell). I've tracked down a .tar.gz driver for it. Unfortunately, as I followed the instructions in the install text file, it came up with this error -

checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

I've tried to convert an .rpm file to a .deb and had a completely different problem... but can't get any info on why it didn't work.

Any suggestions?

Cheers

---

### Post by TidusBlade on 2008-03-07
I think theres a problem with your C++ compiler.
Maybe try this:
```
sudo spt-get install build-essential
```
Hope it works for you :)

---

### Post by rift400 on 2008-03-07
Thanks for that... cleared up one problem... only to lead to another...

The next error message reads -

checking for GDK_IMLIB... configure: error: Package requirements (imlibgdk) were not met:

No package 'imlibgdk' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_IMLIB_CFLAGS
and GDK_IMLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

What the????? Anyone have any ideas?

Cheers

---

