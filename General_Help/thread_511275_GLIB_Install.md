---
title: "GLIB Install"
date: 2007-07-27
forum: General Help
---

### Post by piccler on 2007-07-27
Anytime I try and ./configure something I get GLIB errors like such

hecking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
*** trying without -lgmodule
checking for glib-config... (cached) no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.

*** If you don't have GLIB, you can get it from [ftp://ftp.gtk.org/pub/glib/](ftp://ftp.gtk.org/pub/glib/)
*** We recommend you get the latest stable GLIB 2 version.
*** Compile and install it, and make sure pkg-config finds it,
*** by adding the path where the .pc file is located to PKG_CONFIG_PATH

configure: error: GLIB is required to build irssi.

It says I have the most current version of GLIB installed.

I'm new to this so can someone help me and explain what to do thanks.

Brian
-

EDIT:

I think i fixed that part now I am getting this error

configure: checking "location of ncurses.h file"...
checking for setupterm in -ltinfo... no
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
configure: error: Terminfo/termcap not found - install ncurses-devel package


????? THANKS

---

