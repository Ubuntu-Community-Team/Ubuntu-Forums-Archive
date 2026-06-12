---
title: "Installing Banshee from source"
date: 2006-09-08
forum: General Help
---

### Post by lunchtimemama on 2006-09-08
So I really want to use the Banshee podcasting plugin. I've followed the instructions for [installing from source]("http://patches.ximian.com/Banshee_Source"), but when I run autogen.sh, I get this:

[INDENT]Checking for required M4 macros...
  gnome-compiler-flags.m4 not found
  libtool.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?[/INDENT]

I've installed gnome-common, I've followed the instructions [here]("http://www.ubuntuforums.org/showpost.php?p=1163753&postcount=3"), I've tried every suggestion I can find and nothing works. All of the "not found" .m4 files are in my /usr/share/aclocal. Anyone?

---

### Post by lunchtimemama on 2006-09-09
Anyone?

---

### Post by seppe on 2006-09-13
I found this solution:
[LIST=1]
[*]First I checked where's libtool.m4: [indent][font="monospace"]$ locate libtool.m4
/usr/share/aclocal/libtool.m4
/usr/share/libtool/libtool.m4
[/font][/indent]
[*]Then I executed:
[indent][font="monospace"]env ACLOCAL_FLAGS="-I /usr/share/aclocal" ./autogen.sh[/font][/indent]
[/LIST]

P.S: Maybe you want also to check that you have the *automake1.9* and the *libglib2.0-dev* packages installed

---

### Post by lunchtimemama on 2006-09-14
omgworkslikeacharm

Thank you.

---

### Post by lunchtimemama on 2006-09-15
Now there's a make problem:

[...] error: glib/gstdio.h: No such file or directory [...]

I have gstdio.h in /usr/include/glib-2.0/glib/

Gurus?

---

