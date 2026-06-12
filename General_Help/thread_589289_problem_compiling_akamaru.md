---
title: "problem compiling akamaru"
date: 2007-10-24
forum: General Help
---

### Post by n00b@linux on 2007-10-24
I'm trying to compile Akamaru from source.
This is the first time I've tied compiling on Ubuntu.
I am getting the following error which I fear may be due to a dependency.
However, I'm not sure which one.
Could anyone tell me what dependency I need to install?

```
user@nano-itx:~/akamaru/src/akamaru-build$ sudo ./autogen.sh --prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
libakamaru_la_LDFLAGS: variable `export_symbols' is used but `export_symbols' is undefined
autoreconf: automake failed with exit status: 1
user@nano-itx:~/akamaru/src/akamaru-build$
```

*EDIT*
I found it.  I needed automake1.9.  Gutsy comes with automake1.7.

---

