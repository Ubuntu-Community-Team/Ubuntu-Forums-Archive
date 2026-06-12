---
title: "Which package for gtk+"
date: 2018-01-08
forum: General Help
---

### Post by satimis on 2018-01-08
Hi all,

Ubuntu 16.04 desktop

I have downloaded following package on Epson Website
iscan_2.10.0-1.tar.gz

After extraction
&#10219; ls```

ABOUT-NLS     config.rpath  frontend       ltmain.sh      po
aclocal.m4    config.sub    include        m4             README
AUTHORS       configure     INSTALL        Makefile.am    README.ja
backend       configure.ac  install-sh     Makefile.in    sanei
ChangeLog     COPYING       intl           missing        utils
compile       COPYING.LIB   iscan.spec     mkinstalldirs
config.guess  debian        iscan.spec.in  NEWS
config.h.in   depcomp       lib            NEWS.ja
config.log    doc           libltdl        non-free

```

On terminal ran;
./configure```

....
....
hecking for GTK... configure: error: Package requirements (gtk+) were not met:

No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Please advise which package I need to install?  Thanks

&#10219; ./install-sh ```

./install-sh: no input file specified.

```

Regards
satimis

---

### Post by mc4man on 2018-01-08
Well it would be looking for what's installed from a gtk -dev package, considering the age of that source likely libgtk2.0-dev
There will be more missing like libltdl-dev ect.,  though the odds of compiling that source with current libs & gcc is slim to none

---

