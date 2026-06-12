---
title: "Landell 2.0 dependencies"
date: 2006-10-13
forum: General Help
---

### Post by tronica on 2006-10-13
I'm trying to install landell 2.0 and i get this when trying to install the deb from the cmd line

> lyle@ubuntu:~$ sudo dpkg -i --force-depends landell0.2_0.2.0-0ubuntu1indt2_i386.deb
(Reading database ... 79193 files and directories currently installed.)
Unpacking landell0.2 (from landell0.2_0.2.0-0ubuntu1indt2_i386.deb) ...
dpkg: error processing landell0.2_0.2.0-0ubuntu1indt2_i386.deb (--install):
 trying to overwrite `/usr/bin/landell', which is also in package landell0.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 landell0.2_0.2.0-0ubuntu1indt2_i386.deb


and then when i went in to remove the old version of landell and saw that 2.0 was listed above it i tried to install it and got this, checkt he attachment. Also i have libdbus-1-2 installed allready.

Any help would be greatly apreciated

---

### Post by tronica on 2006-10-13
anybody, I says it depends on libdbus-1-2 but i have that installed.

---

### Post by tronica on 2006-10-13
bump

---

### Post by tronica on 2006-10-15
someone told me that i may need to create a symlink to this version of libdbus? if so how do i do that?

---

### Post by nikhilk on 2006-10-15
The standard install path for libraries is "/usr/lib". First find out where the libdbus library is located. You require to create a symlink only if libdbus is not installed in "/usr/lib".

---

### Post by tronica on 2006-10-15
still no luck, i'm getting a dependencie error that it needs libxss?

---

### Post by suoko on 2007-10-11
I'm also experiencing problems with prepackaged deb of landell due to libdbus.
After I succesfully installed  tapioca-sharp and telepathy-sharp from svn
[see [http://tapioca-voip.sourceforge.net/wiki/index.php/Landell]](http://tapioca-voip.sourceforge.net/wiki/index.php/Landell])
I'm now trying to install svn version of landell
svn checkout [https://tapioca-voip.svn.sourceforge.net/svnroot/landell/trunk/landell](https://tapioca-voip.svn.sourceforge.net/svnroot/landell/trunk/landell) 

but I get this error:

[INDENT]Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running aclocal-1.9...
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
aclocal:configure.ac:93: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.ac:93: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.[/INDENT]

---

