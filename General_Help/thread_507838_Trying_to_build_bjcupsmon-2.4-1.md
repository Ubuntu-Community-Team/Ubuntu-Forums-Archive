---
title: "Trying to build bjcupsmon-2.4-1"
date: 2007-07-23
forum: General Help
---

### Post by Seisen on 2007-07-23
I am trying to build bjcupsmon-2.4-1 but I got this error does anybody understand what it means and how to fix it.

```
michael@ubuntu:~/Desktop/bjcupsmon-2.4-1$ ./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
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

Making ./aclocal.m4 writable ...
Running aclocal  ...
aclocal:configure.in:14: warning: macro `AM_PATH_GTK' not found in library
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
backend/Makefile.am: installing `./depcomp'
backend/Makefile.am:9: `CFLAGS' is a user variable, you should not override it;
backend/Makefile.am:9: use `AM_CFLAGS' instead.
configure.in:24: installing `./config.guess'
configure.in:24: installing `./config.sub'
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./AUTHORS' not found
Running autoconf ...
configure.in:14: error: possibly undefined macro: AM_PATH_GTK
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 5527: syntax error near unexpected token `1.2.0,'
./configure: line 5527: `AM_PATH_GTK(1.2.0, ,'

```

---

