---
title: "Problem with installing luminocity"
date: 2005-04-14
forum: General Help
---

### Post by Promethe on 2005-04-14
When I'm following [these](http://forums.gentoo.org/viewtopic-t-313926-highlight-luminocity.html) instructions I recive this error: 
```
*** Configuring Xau *** [11/24]

./autogen.sh --prefix /home/promethe/luminocity/opt/luminocity  --enable-maintainer-mode --disable-static
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal-1.7  --output=aclocal.m4t
aclocal: configure.ac: 37: macro `AM_PROG_LIBTOOL' not found in library
autoreconf: aclocal-1.7 failed with exit status: 1
```
I've installed autoreconf and aclocal in this version. But it don't want work... Why?

---

### Post by Promethe on 2005-04-15
Anyone?

Solved: You just need to install newest libtool.

---

### Post by Yamakazi on 2005-04-22
OMG thx

Gonna try that one tonight.
I searched like an half hour for the answer on that question yesterday.
I installed every version of auto-make even compiled it from source.

Did you get Luminocity running??  Can you tell us exactly how you did it??
Because this package isn't in the repository:

autoconf-1.7

Which did you use??


How did you start Luminocity?
Which variables to set??

Do you actually type this:

[PHP]cd ../src/
Xfake :1 -ac &
DISPLAY=:1 xterm &
luminocity :1[/PHP] 


TIA



EDIT:  Which libtool are you actually running?  1.5.6-5?

---

