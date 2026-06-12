---
title: "FontConfig Install Problem"
date: 2007-03-09
forum: General Help
---

### Post by SonicTheHedgehog on 2007-03-09
I was installing FontConfig on my computer.  When I typed './configure' i got the following:

```
configure: WARNING: Cannot find usable expat library. Trying to use libxml2 as fallback.
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBXML2... configure: error: Package requirements (libxml-2.0 >= 2.6) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBXML2_CFLAGS
and LIBXML2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

What's wrong?  How do I fix it?  Both libxml2 and libexpat1 are installed.

---

### Post by SonicTheHedgehog on 2007-03-09
*bump*

---

### Post by yabbadabbadont on 2007-03-09
Fontconfig is in the repositories.  Why are you trying to compile it?  (especially since you don't seem to know how to resolve configure errors...  :D)

OK, now for the solution.  Debian packages usually come in two flavors.  The normal one, which you have installed, and the development version, which you don't.  Use synaptic or adept to search for those library files and you will see that there is a libxml-2.0-dev package.  Likewise for the other library.  I hope that helps.

---

### Post by SonicTheHedgehog on 2007-03-09
Well, for one reason, the computer I'm working with isn't connected to the internet (yet).  So, I have to download things off another computer then transfer the files.  I'll see if the dev package of libxml2 helps...

---

