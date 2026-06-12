---
title: "unable to launch application after install"
date: 2007-02-07
forum: General Help
---

### Post by nickoli_02 on 2007-02-07
Hey guys, I followed method 1 of this guide here:

[http://ubuntuforums.org/showthread.php?t=199250&highlight=CREATIVE+ZEN+vision+m+gnomad]("http://ubuntuforums.org/showthread.php?t=199250&highlight=CREATIVE+ZEN+vision+m+gnomad")

so that I can use my Creative Zen Vision: M with Gnomad2. All steps completed smoothly, no troubles, however I can't seem to launch Gnomad2... there is no launcher in the applications menu and when I type gnomad2 in the terminal, I get this:

```
gnomad2
bash: gnomad2: command not found

```

So, any ideas? This is probably a stupid little thing like gnomad2 not being added to the PATH variable but I'm not exactly sure how to check for this stuff... I'd appreciate your help :)

---

### Post by nickoli_02 on 2007-02-07
ugh

bump

---

### Post by llamakc on 2007-02-07
In the terminal, type:

dpkg -L gnomad2

and it will list where all of the files are. You could also try `which gnomad2` (and if that returns nothing, maybe run `sudo updatedb` and try `which gnomad2` again).

---

### Post by nickoli_02 on 2007-02-07
Thanks for the help :)

```
$ dpkg -L gnomad2
Package `gnomad2' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

So gnomad2 didn't get installed...

I went back through the install starting with make, and this is what I found... I'm quite sure I didnt see these errors before though.

```
$ make
Making all in src
make[1]: Entering directory `/home/nwhidden/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/nwhidden/gnomad_install/gnomad2-2.8.10/src'
make: *** [all-recursive] Error 1

```

The issue may be my version of gcc, not sure. I have two versions, gcc-3.4.6 which I need to compile code for a university course, and the newest prerelease gcc-4.1.2. I'm quite sure make will use gcc-4.1.2. So, any ideas? :)

---

### Post by dixon on 2007-03-15
nickoli_02: I've got the same problem :(  Have you found any solution???

---

### Post by genti on 2007-03-16
I have the same problem :(

---

### Post by genti on 2007-03-16
Solved :))))

First remove gnomad2 and libmtp2 that comes with Synaptic, either Complete Removal or the aptitude purge command below.

[http://www.linuxquestions.org/questions/showthread.php?t=518976&page=2](http://www.linuxquestions.org/questions/showthread.php?t=518976&page=2)

Note that there is an updated version of libmtp (libmtp-0.1.4.tar.gz)
Try using that one, if it does not work use the libmtp-0.1.3.tar.gz

DO NOT skip that ./configure --prefix=/usr part, otherwise it will complain that libmtp.so.5 is missing. You could probably create a link but where and why?

My wifi SSID is UbuntuRocks :guitar:

---

### Post by llamakc on 2007-03-16
My bad. I thought you installed a deb.

Glad to hear genti solved it.

---

### Post by dixon on 2007-03-17
THX genti !!! Finally it's working :)

---

