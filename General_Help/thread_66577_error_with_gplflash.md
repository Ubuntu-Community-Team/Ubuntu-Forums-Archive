---
title: "error with gplflash"
date: 2005-09-17
forum: General Help
---

### Post by freemanen on 2005-09-17
i get this error with gplflash2. what could I do about it? And how do i find help about it?

./autogen.sh
/usr/local/share/aclocal/imlib.m4:9: warning: underquoted definition of AM_PATH_IMLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending%20aclocal](http://sources.redhat.com/automake/automake.html#Extending%20aclocal)
/usr/local/share/aclocal/imlib.m4:167: warning: underquoted definition of AM_PATH_GDK_IMLIB
aclocal:configure.in:31: warning: macro `AM_PATH_SDL' not found in library
aclocal:configure.in:37: warning: macro `AM_PATH_XML2' not found in library
configure.in:19: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:20: error: possibly undefined macro: AC_PROG_LIBTOOL
configure.in:31: error: possibly undefined macro: AM_PATH_SDL
configure.in:33: error: possibly undefined macro: AC_MSG_ERROR
configure.in:34: error: possibly undefined macro: AC_CHECK_FT2
configure.in:37: error: possibly undefined macro: AM_PATH_XML2
autoreconf: /usr/local/bin/autoconf failed with exit status: 1

---

### Post by transporter_ii on 2007-12-31
Ubuntu 7.10 Gutsy

Got this error and wasted hours on it. 

Did a "which libtool," and got nothing. Duh, it isn't installed.

How to install libtool:

sudo aptitude install libtool

Did not get the undefined macro error after this.

Note some other things I had to install to get stuff to work:

sudo apt-get install autoconf automake make g++
sudo apt-get install autoconf

Transporter_ii

---

