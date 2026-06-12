---
title: "Gaim 2.0 beta3 GTK+ Error"
date: 2006-07-03
forum: General Help
---

### Post by anandrd on 2006-07-03
I tried to compile gaim 2.0 beta3 from source and I am getting the following -

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.
configure: error:
*** GTK+ 2.0 is required to build Gaim; please make sure you have the GTK+
*** development headers installed. The latest version of GTK+ is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).

I checked and I have libgtk2.0-dev installed. Any help?

---

### Post by mlind on 2006-07-03
That library should do it, try reinstalling it or something.

Other dependencies are (from debian/control)
```

 libgtk2.0-dev, libxss-dev, libmeanwhile-dev, libgadu-dev (>= 1:1.6+20060215-1),
 libgnutls11-dev (>= 1.0.16-5), tcl8.4-dev, tk8.4-dev, libao-dev,
 libaudiofile-dev, libgtkspell-dev, libltdl3-dev, libperl-dev,
 libstartup-notification0-dev, xutils, libzephyr-dev, libxml2-dev,
 libebook1.2-dev, libedata-book1.2-dev, libcamel1.2-dev,
 libdbus-glib-1-dev, dbus, python2.4, libavahi-compat-howl-dev,
 libxml-parser-perl

```

You must compile newer version of libgadu too.

---

### Post by anandrd on 2006-07-03
[QUOTE=mlind]That library should do it, try reinstalling it or something.

[\QUOTE]

I reinstalled it. Still no luck..

---

### Post by mlind on 2006-07-04
[QUOTE=anandrd]
I reinstalled it. Still no luck..[/QUOTE]

Strange.. You could try using this [guide]("http://www.ubuntuforums.org/showthread.php?t=204523") i wrote earlier if it works for you.
I suggest you to discard the debfoster stuff, and build using  [pbuilder]("http://www.ubuntuforums.org/showthread.php?t=206382") instead.

---

### Post by anandrd on 2006-07-18
Aptitude seems to be much more clever in resolving dependencies. "sudo aptitude install libgtk2.0-dev" solved the problem. It had to downgrade some libraries to do that.

---

