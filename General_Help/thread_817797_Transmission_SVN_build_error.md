---
title: "Transmission SVN build error"
date: 2008-06-03
forum: General Help
---

### Post by smmalis on 2008-06-03
I'm trying to build and install the latest version of Transmission from their SVN repo.  However, I keep getting build errors.  I have written a script for the install, which is attached, but all the code was copied from a script for another program (with a couple minor changes).  Whenever I run ./autogen.sh I get the following output:
```
configure.in:27: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
Creating aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Making aclocal.m4 writable ...
Running intltoolize...
Running ./configure --enable-maintainer-mode
autogen.sh: 46: ./configure: not found

Now type 'make' to compile Transmission.
```

---

