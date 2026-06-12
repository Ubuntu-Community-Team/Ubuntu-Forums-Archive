---
title: "problems with  ./autogen.sh and gplflash"
date: 2005-07-07
forum: General Help
---

### Post by freemanen on 2005-07-07
when i type sudo ./autogen.sh  I get this error 

configure.in:19: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:20: error: possibly undefined macro: AC_PROG_LIBTOOL
configure.in:33: error: possibly undefined macro: AC_MSG_ERROR
configure.in:34: error: possibly undefined macro: AC_CHECK_FT2
autoreconf: /usr/bin/autoconf failed with exit status: 1

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

