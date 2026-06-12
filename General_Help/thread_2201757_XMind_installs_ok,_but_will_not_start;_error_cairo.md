---
title: "XMind installs ok, but will not start; error cairo-surface.c: failed"
date: 2014-01-25
forum: General Help
---

### Post by David_Sloboda on 2014-01-25
Hello. I have Lubuntu 12.04  on i386 and I am unable to get XMind to start.

32bit XMind .deb package will install without error.
[http://www.xmind.net/download/linux/](http://www.xmind.net/download/linux/)


I start the application, I get the splash screen, the XMind GUI comes up for about two seconds, then it crashes.

Starting it from the command line, I get the following error message:

```
david@anyanka:~/bin/xmind/XMind_Linux$ ./XMind 
XMind: /build/buildd/cairo-1.10.2/src/cairo-surface.c:385: _cairo_surface_begin_modification: Assertion `! surface->finished' failed.
Aborted (core dumped)
david@anyanka:~/bin/xmind/XMind_Linux$

```

There is a libcairo-swt.so in the Portable directory, 
but I do not know how to tell the XMind binary to reference that shared object,
or even if that is related to the issue.

```

david@anyanka:~/bin/xmind/XMind_Linux$ ls -al
total 552
drwxr-xr-x 5 david david   4096 Jan 25 17:03 .
drwxrwxr-x 7 david david   4096 Jan 25 16:59 ..
drwxr-xr-x 2 david david   4096 Jan 22 19:26 about_files
-rw-r--r-- 1 david david    577 Nov 20  2012 about.html
-rw-r--r-- 1 david david 199145 Jan 22 19:26 artifacts.xml
drwxr-xr-x 8 david david   4096 Jan 25 17:03 configuration
-rw-r--r-- 1 david david    117 Jan 22 19:18 .eclipseproduct
-rwxr-xr-x 1 david david 266168 Nov 20  2012 libcairo-swt.so
drwxr-xr-x 4 david david   4096 Jan 22 19:26 p2
-rwxr-xr-x 1 david david  63050 Nov 20  2012 XMind
-rw-r--r-- 1 david david    321 Jan 22 19:28 XMind.ini
david@anyanka:~/bin/xmind/XMind_Linux$ 

```

The same error shows up when I try the "Portable" version of the software.
[http://www.xmind.net/download/portable/](http://www.xmind.net/download/portable/)

Has anyone seen this sort of error before?

Is this related to a version of GTK not being correct?
The command
$ dpkg --get-selections | grep -v deinstall | grep -i gtk
implies that I have gtk2 and gtk3 installed.

I have searched for the cairo-1.10.2/src/cairo-surface.c error on Google and not found a fix yet.

Thank you,
David Sloboda

---

### Post by tgalati4 on 2014-01-25
I installed it on Linux Mint 14 Mate (based on 12.10) 64-bit and it does the same thing.  The version of libcairo-swt.so is the same:

-rwxr-xr-x  1 root root 335360 Nov 20  2012 libcairo-swt.so

It's bigger because it is 64-bit.  I would send an email to the developers.  Looks like a bug.

It's not clear to me why libcairo-swt.so is included with the package.  We have a libcairo framework in Ubuntu.

tgalati4@Mint14-Extensa ~ $ apt-cache search libcairo
libcairo-gobject2 - The Cairo 2D vector graphics library (GObject library)
libcairo-perl - Perl interface to the Cairo graphics library
libcairo-script-interpreter2 - The Cairo 2D vector graphics library (script interpreter)
libcairo2 - The Cairo 2D vector graphics library
libcairo2-dbg - The Cairo 2D vector graphics library (debugging symbols)
libcairo2-dev - Development files for the Cairo 2D graphics library
libcairo2-doc - Documentation for the Cairo Multi-platform 2D graphics library
libcairomm-1.0-1 - C++ wrappers for Cairo (shared libraries)
libcairomm-1.0-dev - C++ wrappers for Cairo (development files)
libcairomm-1.0-doc - C++ wrappers for Cairo (documentation)
libcairo-gobject-perl - integrate Cairo into the Glib type system in Perl
libcairo-ocaml - OCaml bindings for Cairo (runtime)
libcairo-ocaml-dev - OCaml bindings for Cairo
libcairo-ruby - Transitional package for ruby-cairo
libcairo-ruby1.8 - Transitional package for ruby-cairo
ruby-cairo - Cairo bindings for the Ruby language

---

### Post by David_Sloboda on 2014-01-26
I posted a public question on the XMind support site:

[https://xmind.desk.com/customer/en/portal/questions/5293851-xml-will-not-run-on-lubuntu-12-4-error-cairo-surface-c-failed?new=5293851](https://xmind.desk.com/customer/en/portal/questions/5293851-xml-will-not-run-on-lubuntu-12-4-error-cairo-surface-c-failed?new=5293851)

---

### Post by David_Sloboda on 2014-01-28
Posting on the XMind support site led to a response.

[COLOR=#000000][FONT=Lucida Sans Unicode]Installing 3.4.0 resolved the issue. XMind 3.4.0 starts on Lubuntu 12.04 without problem.[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-01-28
3.4.1 is out now, so it looks like it is undergoing rapid development.

---

