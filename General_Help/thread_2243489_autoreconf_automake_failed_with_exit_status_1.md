---
title: "autoreconf: automake failed with exit status: 1"
date: 2014-09-09
forum: General Help
---

### Post by captin on 2014-09-09
Hello,

I'm working on installing a honeypot in my ec2 instance from AWS, I use Ubuntu Server 14.04 LTS (HVM) as my OS.

during my istallation the procedures instructs me to run "autoreconf -vi" however, I got error, which I could not resolve. Below is the result of my terminal 


ubuntu@ip-0-0-0-0:/opt/dionaea/liblcfg/code$ sudo autoreconf -vi
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:8: warning: AM_INIT_AUTOMAKE: two- and three-arguments forms are deprecated.  For more info, see:
configure.ac:8: [http://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation](http://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation)
src/Makefile.am:7: error: Libtool library used but 'LIBTOOL' is undefined
src/Makefile.am:7:   The usual way to define 'LIBTOOL' is to add 'LT_INIT'
src/Makefile.am:7:   to 'configure.ac' and run 'aclocal' and 'autoconf' again.
src/Makefile.am:7:   If 'LT_INIT' is in 'configure.ac', make sure
src/Makefile.am:7:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1

I have updated the system in case that was the issue, but the I'm still receiving the same error

what shall I do to carry on my work

---

