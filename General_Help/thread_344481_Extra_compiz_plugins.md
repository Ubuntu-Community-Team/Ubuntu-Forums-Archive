---
title: "Extra compiz plugins"
date: 2007-01-23
forum: General Help
---

### Post by matthewthebig on 2007-01-23
I downloaded the compiz-extra-latest.tar.bz2 from [here](http://go-compiz.org/index.php?title=Download). I extracted it and ./configured.

It seems to work fine until the end when it states:```
Package libpng was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libpng', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_EXTRA_CFLAGS
and COMPIZ_EXTRA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

And when I try to make it, it says```
make: *** No targets specified and no makefile found.  Stop.

```
Despite there being a makefile.in and a makefile.am.

Could anyone help?

---

### Post by cracker on 2007-01-23
I think your problem is here:

Package libpng was not found in the pkg-config search path.

Try

sudo apt-get install libpng12-0 libpng12-dev

and then try installing again.

---

