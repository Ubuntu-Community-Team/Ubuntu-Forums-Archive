---
title: "MySQL Gui Tools installation help"
date: 2006-09-25
forum: General Help
---

### Post by reynoldlariza on 2006-09-25
the version of mysql query browser installed by ubuntu package manager is old and crashes everytime i try edit a table or anything... 

I downloaded the GUI package from mysql.com website, but i got error installing it..

```
reynold@rel:~/mysql-gui-tools-5.0r3/mysql-query-browser$ sudo ./configure
Password:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for pkg-config... pkg-config
checking for ../mysql-gui-common/library/base-library/include... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  pt_BR
checking for mysql_config... -I/usr/include/mysql -DBIG_JOINS=1
checking for mysql_config... -L/usr/lib/mysql -lmysqlclient_r -lz -lpthread -lcrypt -lnsl -lm -lpthread
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 libxml-2.0 >= 2.6.2) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

please i need help, coz i always work with PHP and Mysql everyday as this is part of my job... and im a noob with linux. This is frustrating :(

---

### Post by reynoldlariza on 2006-09-25
shucks :(

I looked thru the forum and found that this will really not work with dapper.

I looked at DBDesigner4, looks good, i installed and tried, almost working but seems to fail too, also the font is really a mess.
anyway I had to shift back to winxp since (as of now) it's the best web development enviroment I can get.

[frustrations....]
I tried to see and test if linux is great enough to be developers environment. Looking at the at front door... seems good enough, because of it's reputation as stable OS. But when you got it... crap :( I guess, I'll just back out of proposing it with the team.

---

### Post by iluminate on 2006-09-26
Have the same problem. Really frustrating that MySQL GUI Tools does not work with dapper.](*,) ](*,) ](*,) ](*,)

---

### Post by nix4me on 2006-09-26
Have you tried using phpmyadmin?

I use it to manage my databases and its quite nice.

nix4me

---

### Post by WitchCraft on 2008-04-25
> **reynoldlariza said:**
> the version of mysql query browser installed by ubuntu package manager is old and crashes everytime i try edit a table or anything... 

I downloaded the GUI package from mysql.com website, but i got error installing it..

```
reynold@rel:~/mysql-gui-tools-5.0r3/mysql-query-browser$ sudo ./configure
Password:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for pkg-config... pkg-config
checking for ../mysql-gui-common/library/base-library/include... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  pt_BR
checking for mysql_config... -I/usr/include/mysql -DBIG_JOINS=1
checking for mysql_config... -L/usr/lib/mysql -lmysqlclient_r -lz -lpthread -lcrypt -lnsl -lm -lpthread
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... configure: error: Package requirements (glib-2.0 libxml-2.0 >= 2.6.2) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

please i need help, coz i always work with PHP and Mysql everyday as this is part of my job... and im a noob with linux. This is frustrating :(

root@all:~# apt-file search glib-2.0
```

libglib2.0-0: /usr/lib/libglib-2.0.so.0
libglib2.0-0: /usr/lib/libglib-2.0.so.0.1600.3
libglib2.0-0-dbg: /usr/lib/debug/usr/lib/libglib-2.0.so.0.1600.3
libglib2.0-dev: /usr/include/glib-2.0/gio/gappinfo.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gasyncresult.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gbufferedinputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gbufferedoutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gcancellable.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gcontenttype.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gdatainputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gdataoutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gdrive.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfile.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileattribute.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileenumerator.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileicon.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileinfo.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileinputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfilemonitor.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfilenamecompleter.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfileoutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfilterinputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gfilteroutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gicon.h
libglib2.0-dev: /usr/include/glib-2.0/gio/ginputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gio.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gioenumtypes.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gioerror.h
libglib2.0-dev: /usr/include/glib-2.0/gio/giomodule.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gioscheduler.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gloadableicon.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gmemoryinputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gmemoryoutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gmount.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gmountoperation.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gnativevolumemonitor.h
libglib2.0-dev: /usr/include/glib-2.0/gio/goutputstream.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gseekable.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gsimpleasyncresult.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gthemedicon.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gvfs.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gvolume.h
libglib2.0-dev: /usr/include/glib-2.0/gio/gvolumemonitor.h
libglib2.0-dev: /usr/include/glib-2.0/glib-object.h
libglib2.0-dev: /usr/include/glib-2.0/glib.h
libglib2.0-dev: /usr/include/glib-2.0/glib/galloca.h
libglib2.0-dev: /usr/include/glib-2.0/glib/garray.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gasyncqueue.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gatomic.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gbacktrace.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gbase64.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gbookmarkfile.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gcache.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gchecksum.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gcompletion.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gconvert.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gdataset.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gdate.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gdir.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gerror.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gfileutils.h
libglib2.0-dev: /usr/include/glib-2.0/glib/ghash.h
libglib2.0-dev: /usr/include/glib-2.0/glib/ghook.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gi18n-lib.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gi18n.h
libglib2.0-dev: /usr/include/glib-2.0/glib/giochannel.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gkeyfile.h
libglib2.0-dev: /usr/include/glib-2.0/glib/glist.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmacros.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmain.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmappedfile.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmarkup.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmem.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gmessages.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gnode.h
libglib2.0-dev: /usr/include/glib-2.0/glib/goption.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gpattern.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gprimes.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gprintf.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gqsort.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gquark.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gqueue.h
libglib2.0-dev: /usr/include/glib-2.0/glib/grand.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gregex.h
libglib2.0-dev: /usr/include/glib-2.0/glib/grel.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gscanner.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gsequence.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gshell.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gslice.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gslist.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gspawn.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gstdio.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gstrfuncs.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gstring.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gtestutils.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gthread.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gthreadpool.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gtimer.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gtree.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gtypes.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gunicode.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gurifuncs.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gutils.h
libglib2.0-dev: /usr/include/glib-2.0/glib/gwin32.h
libglib2.0-dev: /usr/include/glib-2.0/gmodule.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gboxed.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gclosure.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/genums.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gmarshal.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gobject.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gobjectnotifyqueue.c
libglib2.0-dev: /usr/include/glib-2.0/gobject/gparam.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gparamspecs.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gsignal.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gsourceclosure.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gtype.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gtypemodule.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gtypeplugin.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gvalue.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gvaluearray.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gvaluecollector.h
libglib2.0-dev: /usr/include/glib-2.0/gobject/gvaluetypes.h
libglib2.0-dev: /usr/lib/glib-2.0/include/glibconfig.h
libglib2.0-dev: /usr/lib/libglib-2.0.a
libglib2.0-dev: /usr/lib/libglib-2.0.la
libglib2.0-dev: /usr/lib/libglib-2.0.so
libglib2.0-dev: /usr/lib/pkgconfig/glib-2.0.pc
libglib2.0-dev: /usr/share/aclocal/glib-2.0.m4
libglib2.0-dev: /usr/share/glib-2.0/gettext/mkinstalldirs
libglib2.0-dev: /usr/share/glib-2.0/gettext/po/Makefile.in.in
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/glib-object.h
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/glib.h
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/glib/gprintf.h
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/glib/gstdio.h
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/gmodule.h
lsb-build-desktop3: /usr/include/lsb3/glib-2.0/gobject/gvaluecollector.h
lsb-build-desktop3: /usr/lib/lsb3/libglib-2.0.so
lsb-build-desktop3: /usr/lib/lsb3/pkgconfig/glib-2.0.pc
valac: /usr/share/vala/vapi/glib-2.0.vapi
root@all:~# 

```

apt-get install libglib2.0-dev

---

