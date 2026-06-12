---
title: "strange problems trying to compile an extension to pidgin"
date: 2007-08-26
forum: General Help
---

### Post by spiroth10 on 2007-08-26
I wasn't sure what to title this thread aptly... Anyway, I've been a linux user for a long time now (years...) and I've yet to encounter a similar error yet. I was trying to install msimprpl-0.15, which is a pidgin extension for the myspaceim protocol...

so I do the usual sudo ./autogen.sh, and fill the dependencies as needed, then I get this message:

```
josh@josh-desktop:~/Desktop/msimprpl-0.15.tar.gz_FILES$ sudo ./autogen.sh
Generating configuration files for Pidgin, please wait....

Running libtoolize, please ignore non-fatal messages....
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

You should add the contents of '/usr/share/aclocal/intltool.m4' to 'aclocal.m4'.
aclocal: configure.ac: 564: macro `AM_GCONF_SOURCE_2' not found in library

```

no idea how to fix it, nor why its giving me the error...

any idea why? I do have build-essential installed, I compile lots of stuff, I'm used to it lol.

---

### Post by spiroth10 on 2007-08-27
*bump*

sorry for bumping it, I still have not resolved the issue...

---

### Post by lgespee on 2007-10-03
Try installing the packages "intltool" and "gnome-common".
Maybe that helps.

---

