---
title: "glib path"
date: 2004-11-14
forum: General Help
---

### Post by dubdubdub on 2004-11-14
I am tring to install a cursor enhancement (gcursor) that i obtained from gnomefiles. I get this error when I run ./Configure:
> 
        ... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found


I am sure this is an easy fix!
thanks in advance

---

### Post by sfw5000 on 2004-11-15
Are you sure you have glib installed? Use synaptic or apt to make sure it is installed. 
```
sudo apt-cache search glib
```

---

### Post by dubdubdub on 2004-11-15
If "libglib" is it, then yes it is listed. 

```

dub@ubuntu:~ $ sudo apt-cache search glib
Password:
libdb1-compat - The Berkeley database routines [glibc 2.0/2.1 compatibility]
libglib1.2 - The GLib library of C routines
libglib1.2-dbg - GLib libraries and debugging symbols
libglib1.2-dev - Development files for GLib library
libgnet-dev - Developer files for GNet network library
libgnet2.0-0 - GNet network library
libnss-db - DB Name Service Module
libwww-dev - The W3C WWW library - development files
libwww-ssl-dev - The W3C WWW library - development files (SSL support)
abicheck - binary compatibility checking tool
firebird-c32-server - FireBird Classic w/ 32bit I/O - RDBMS based on InterBase 6.0 code
firebird-c64-server - FireBird Classic w/ 64bit I/O - RDBMS based on InterBase 6.0 code
firebird-s32-server - FireBird Super w/ 32bit I/O - RDBMS based on InterBase 6.0 code
firebird-s64-server - FireBird Super w/ 64bit I/O - RDBMS based on InterBase 6.0 code
free-java-sdk - Complete Java SDK environment consisting of free Java tools
ja-trans - Japanese gettext message files
libarts1-mpeglib - mpeglib is a mp3 and mpeg I video/audio library (Arts plugin)libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libgetopt-java - GNU getopt - Java port
libglib-cil - .NET binding for the GLib utility library
libglib1.2-doc - Documentation files for the GLib library version 1.2
libroy-dev - Utility and data structure library (development files)
libroy1 - Utility and data structure library (runtime files)
libroy1-dbg - Utility and data structure library (debugging files)
libroy1-prof - Utility and data structure library (profiling files)
libstdc++2.10-glibc2.2 - The GNU stdc++ library
mpeglib - mp3 and mpeg I video/audio library for linux
python-utmp - python module for working with utmp
acroread-plugin - Adobe Acrobat(R) Reader plugin for mozilla / konqueror
dbus-1 - simple interprocess messaging system
dbus-glib-1 - simple interprocess messaging system (GLib-based shared library)
dbus-glib-1-dev - simple interprocess messaging system (GLib interface)
gftp-gtk - X/GTK+ FTP client
glibc-doc - GNU C Library: Documentation
libc6 - GNU C Library: Shared libraries and Timezone data
libc6-pic - GNU C Library: PIC archive library
libglib2.0-0 - The GLib library of C routines
libglib2.0-data - Common files for GLib library
libglib2.0-dbg - The GLib libraries and debugging symbols
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library
libglibmm-2.4-1 - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libgnomecups1.0-1 - GNOME library for CUPS interaction
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
libsoup2.2-7 - an HTTP library implementation in C -- Shared library
libsoup2.2-dev - an HTTP library implementation in C -- Development files
linux-kernel-headers - Linux Kernel Headers for development
manpages-dev - Manual pages about using GNU/Linux for development
bglibs-dev - Bruce Guenter's one stop library package
bglibs-doc - Bruce Guenter's one stop library package (documentation)
classpath-common - GNU Classpath - architecture independent files
devhelp-book-glibc - GNU C Library (glibc) book for the DevHelp system
devhelp-book-gtk2 - Gtk+ 2 books for the DevHelp system
gftp - X/GTK+ FTP client
gftp-text - colored FTP client using GLib
kmtrace - a KDE memory leak tracer
libgfccore-2.0-0 - GTK+ Foundation Classes Core - shared libraries
libgfccore-2.0-0-dbg - GTK+ Foundation Classes Core - debug symbols
libgfccore-dev - GTK+ Foundation Classes Core - development files
libgfccore-doc - GTK+ Foundation Classes Core - API reference documentation
libghc6-missingh-dev - Library of utility functions for Haskell, GHC6 package
libglib-perl - Perl interface to the GLib and GObject libraries
libglib2-ruby - Glib 2 bindings for the Ruby language
libgnetwork1.0-0 - networking wrapper library using Glib/GObject
libgnetwork1.0-dev - networking wrapper library using Glib/GObject (development files)
libhugs-missingh - Library of utility functions for Haskell, Hugs package
libmissinglib-ocaml-dev - Library of utility functions for OCaml
libnss-ldap - NSS module for using LDAP as a naming service
libnss-pgsql1 - name service switch module using PostgreSQL
libpolyp0-glib2.0 - Library for the polypaudio sound server
libpolyp0-glib2.0-dev - Library for the polypaudio sound server
libsoup2.0-0 - an HTTP library implementation in C -- Shared library
libsoup2.0-dev - an HTTP library implementation in C -- Development files
libsoup2.2-doc - an HTTP library implementation in C -- API Reference
libtag1 - TagLib Audio Meta-Data Library
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libuclibc-dev - A small implementation of the C library
libuclibc0 - A small implementation of the C library
linuxinfo - Displays extended system information
manpages-pl-dev - Polish man pages for developers
missingh-doc - Documentation for Haskell utility library
perdition-dev - Development libraries and headers for perdition
perdition-ldap - Library to allow perdition to access LDAP based popmaps
perdition-mysql - Library to allow perdition to access MySQL based popmaps
perdition-odbc - Library to allow perdition to access ODBC based popmaps
perdition-postgresql - Library to allow perdition to access PostgreSQL based popmaps
winbind - service to resolve user and group information from Windows NT servers
dub@ubuntu:~ $

```

---

### Post by Ste on 2005-01-01
[QUOTE=dubdubdub]If "libglib" is it, then yes it is listed. 

```

dub@ubuntu:~ $ sudo apt-cache search glib
Password:
libdb1-compat - The Berkeley database routines [glibc 2.0/2.1 compatibility]
libglib1.2 - The GLib library of C routines
libglib1.2-dbg - GLib libraries and debugging symbols
libglib1.2-dev - Development files for GLib library
libgnet-dev - Developer files for GNet network library
libgnet2.0-0 - GNet network library
libnss-db - DB Name Service Module
libwww-dev - The W3C WWW library - development files
libwww-ssl-dev - The W3C WWW library - development files (SSL support)
abicheck - binary compatibility checking tool
firebird-c32-server - FireBird Classic w/ 32bit I/O - RDBMS based on InterBase 6.0 code
firebird-c64-server - FireBird Classic w/ 64bit I/O - RDBMS based on InterBase 6.0 code
firebird-s32-server - FireBird Super w/ 32bit I/O - RDBMS based on InterBase 6.0 code
firebird-s64-server - FireBird Super w/ 64bit I/O - RDBMS based on InterBase 6.0 code
free-java-sdk - Complete Java SDK environment consisting of free Java tools
ja-trans - Japanese gettext message files
libarts1-mpeglib - mpeglib is a mp3 and mpeg I video/audio library (Arts plugin)libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libgetopt-java - GNU getopt - Java port
libglib-cil - .NET binding for the GLib utility library
libglib1.2-doc - Documentation files for the GLib library version 1.2
libroy-dev - Utility and data structure library (development files)
libroy1 - Utility and data structure library (runtime files)
libroy1-dbg - Utility and data structure library (debugging files)
libroy1-prof - Utility and data structure library (profiling files)
libstdc++2.10-glibc2.2 - The GNU stdc++ library
mpeglib - mp3 and mpeg I video/audio library for linux
python-utmp - python module for working with utmp
acroread-plugin - Adobe Acrobat(R) Reader plugin for mozilla / konqueror
dbus-1 - simple interprocess messaging system
dbus-glib-1 - simple interprocess messaging system (GLib-based shared library)
dbus-glib-1-dev - simple interprocess messaging system (GLib interface)
gftp-gtk - X/GTK+ FTP client
glibc-doc - GNU C Library: Documentation
libc6 - GNU C Library: Shared libraries and Timezone data
libc6-pic - GNU C Library: PIC archive library
libglib2.0-0 - The GLib library of C routines
libglib2.0-data - Common files for GLib library
libglib2.0-dbg - The GLib libraries and debugging symbols
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library
libglibmm-2.4-1 - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libgnomecups1.0-1 - GNOME library for CUPS interaction
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
libsoup2.2-7 - an HTTP library implementation in C -- Shared library
libsoup2.2-dev - an HTTP library implementation in C -- Development files
linux-kernel-headers - Linux Kernel Headers for development
manpages-dev - Manual pages about using GNU/Linux for development
bglibs-dev - Bruce Guenter's one stop library package
bglibs-doc - Bruce Guenter's one stop library package (documentation)
classpath-common - GNU Classpath - architecture independent files
devhelp-book-glibc - GNU C Library (glibc) book for the DevHelp system
devhelp-book-gtk2 - Gtk+ 2 books for the DevHelp system
gftp - X/GTK+ FTP client
gftp-text - colored FTP client using GLib
kmtrace - a KDE memory leak tracer
libgfccore-2.0-0 - GTK+ Foundation Classes Core - shared libraries
libgfccore-2.0-0-dbg - GTK+ Foundation Classes Core - debug symbols
libgfccore-dev - GTK+ Foundation Classes Core - development files
libgfccore-doc - GTK+ Foundation Classes Core - API reference documentation
libghc6-missingh-dev - Library of utility functions for Haskell, GHC6 package
libglib-perl - Perl interface to the GLib and GObject libraries
libglib2-ruby - Glib 2 bindings for the Ruby language
libgnetwork1.0-0 - networking wrapper library using Glib/GObject
libgnetwork1.0-dev - networking wrapper library using Glib/GObject (development files)
libhugs-missingh - Library of utility functions for Haskell, Hugs package
libmissinglib-ocaml-dev - Library of utility functions for OCaml
libnss-ldap - NSS module for using LDAP as a naming service
libnss-pgsql1 - name service switch module using PostgreSQL
libpolyp0-glib2.0 - Library for the polypaudio sound server
libpolyp0-glib2.0-dev - Library for the polypaudio sound server
libsoup2.0-0 - an HTTP library implementation in C -- Shared library
libsoup2.0-dev - an HTTP library implementation in C -- Development files
libsoup2.2-doc - an HTTP library implementation in C -- API Reference
libtag1 - TagLib Audio Meta-Data Library
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libuclibc-dev - A small implementation of the C library
libuclibc0 - A small implementation of the C library
linuxinfo - Displays extended system information
manpages-pl-dev - Polish man pages for developers
missingh-doc - Documentation for Haskell utility library
perdition-dev - Development libraries and headers for perdition
perdition-ldap - Library to allow perdition to access LDAP based popmaps
perdition-mysql - Library to allow perdition to access MySQL based popmaps
perdition-odbc - Library to allow perdition to access ODBC based popmaps
perdition-postgresql - Library to allow perdition to access PostgreSQL based popmaps
winbind - service to resolve user and group information from Windows NT servers
dub@ubuntu:~ $

```[/QUOTE]
 Sorry to drag up an old post but I'm having this same problem.
Have compiled Glib 2.6.0 from source but other packages can't find it.

---

### Post by randy on 2005-01-01
If your installing using a package you'll need the libglib2 development package.  If your installing from source and you didn't specify a prefix it'll be under /usr/local/lib/pkgconfig.  You'll need to add that directory to your pkgconfig path.

---

### Post by Ste on 2005-01-01
[QUOTE=randy]If your installing using a package you'll need the libglib2 development package.  If your installing from source and you didn't specify a prefix it'll be under /usr/local/lib/pkgconfig.  You'll need to add that directory to your pkgconfig path.[/QUOTE]
 I'm installing from source. When you say add it to my pkgconfig path what exactly did you mean.
I edited /usr/local/lib/pkgconfig/glib2.pc or something but that didn't work.

I feel I've tried everything.

The latest packages don't go up as high as glib 2.6 and I need it for some new packages, Gens for example as there are no packages for it in the repos but there are for zsnes. [/end rant]

---

### Post by pwhysall on 2005-01-01
[QUOTE=dubdubdub]I am tring to install a cursor enhancement (gcursor) that i obtained from gnomefiles. I get this error when I run ./Configure:


I am sure this is an easy fix!
thanks in advance[/QUOTE]
Do you have libglib2.0-dev installed?

"dpkg -l | grep libglib2" will show you.

One solution would be to install the "gnome-devel" package, which depends on all the bits and pieces you need to compile GNOME programs. And when I say "all", I mean "all, for very large values of all" ;)

---

### Post by Ste on 2005-01-02
[QUOTE=pwhysall]Do you have libglib2.0-dev installed?

"dpkg -l | grep libglib2" will show you.

One solution would be to install the "gnome-devel" package, which depends on all the bits and pieces you need to compile GNOME programs. And when I say "all", I mean "all, for very large values of all" ;)[/QUOTE]

THANK YOU.
It passed it this morning when compiling atk fot gtk.
Apt-get install libglib2.0-dev worked a treat.

---

### Post by kayaker on 2005-01-09
[QUOTE=randy]If your installing using a package you'll need the libglib2 development package.  If your installing from source and you didn't specify a prefix it'll be under /usr/local/lib/pkgconfig.  You'll need to add that directory to your pkgconfig path.[/QUOTE]
Here is my /usr/local/lib/pkgconfig/glib-2.0.pc file.

> prefix=/usr/local
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include

glib_genmarshal=glib-genmarshal
gobject_query=gobject-query
glib_mkenums=glib-mkenums

Name: GLib
Description: C Utility Library
Version: 2.6.1
Libs: -L${libdir} -lglib-2.0  
Cflags: -I${includedir}/glib-2.0 -I${libdir}/glib-2.0/include 

How do I "add that directory to [my] pkgconfig path"? What directory? Where do I add it? 

Thanks

NOOB

---

### Post by kayaker on 2005-01-09
More from me...

Here's what I get when I try ./configure on atk-1.9.0 same that I get when I try ./configure on pango-1.8.0

> checking for GLIB - version >= 2.5.7... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

Obviously ubutnu isn't seeing the glib-2.6.0 that I just installed. Is there a pakage for all this stuff from the package manager, or online somewhere?

I'm aiming for gtk+ so I can try gtkPod.

---

