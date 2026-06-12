---
title: "Cannot compile AWN...something wrong with my system build"
date: 2007-09-28
forum: General Help
---

### Post by eitan_a on 2007-09-28
Hi guys, I am trying to compile the latest version of AWN but cannot, and when I do successfully compile I get an error.  Here is the ouput from my ./autogen.sh 

```


checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.61

checking for automake >= 1.9...

  testing automake-1.10... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.4.3...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.9.6

checking for intltool >= 0.25...

  testing intltoolize... 
found 0.35.4

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.21

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.in


Running libtoolize...


Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running aclocal-1.9...

/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
/usr/local/share/aclocal/gdk-pixbuf.m4:12: warning: underquoted definition of AM_PATH_GDK_PIXBUF


```

And it dies there.  If I do these commands..

export ACLOCAL_FLAGS='-I /usr/share/aclocal'
export ACLOCAL_PATH=/usr/share/local

it compiles successfully.  This already shows to me that something is wierd with my system.

However, although it compiles successfully, when I run avant-window-manager, I get this error..

avant-window-navigator: symbol lookup error: /usr/local/lib/libgdk-x11-2.0.so.0: undefined symbol: g_type_register_static_simple

I have all the dependencies installed.  Also, I can run AWN from trevino's reps but their applets don't work, which is why I want to compile it.  Thanks a million for any help in the right direction.
Eitan

---

### Post by mexlinux on 2007-10-01
Don't know how to solve your problem....
BUT
Treviño has packages of the lastest versions of AWN in his repos.
Youcan try them here:
[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

---

