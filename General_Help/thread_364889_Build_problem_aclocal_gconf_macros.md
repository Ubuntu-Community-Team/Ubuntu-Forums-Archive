---
title: "Build problem: aclocal gconf macros?"
date: 2007-02-18
forum: General Help
---

### Post by fictivetoast on 2007-02-18
Not sure if this is the right place for this, but I'm trying to recompile banshee from svn, and when I run autogen I'm told:

Running aclocal-1.9...
aclocal:configure.ac:38: warning: macro `AM_GCONF_SOURCE_2' not found in library

What does this mean and how can I fix it?

---

### Post by aragorn2909 on 2007-02-18
I'm not positive, but you might want to try installing libgconf2-dev, and see if that clears up that error.

AB

---

### Post by fictivetoast on 2007-02-18
Thank you!  That did help wonderfully...

BUT I'm now being told:

Running aclocal-1.9...
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE


Though autogen seems to disregard this and keep going.  Should I be worried about that?

---

### Post by aragorn2909 on 2007-02-18
Personally, I wouldn't worry too much about it.  See first if everything works otherwise.

AB

---

