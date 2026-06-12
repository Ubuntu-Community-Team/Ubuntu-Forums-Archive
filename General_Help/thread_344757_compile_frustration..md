---
title: "compile frustration."
date: 2007-01-23
forum: General Help
---

### Post by Daandaan on 2007-01-23
I tried to install WifiScanner. The ./configure script did its job well (after 15 minutes of missing libs frustration 8-) ). I ran sudo sh ./autogen.sh. And i get this error.
>>
processing .
aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending%20aclocal](http://sources.redhat.com/automake/automake.html#Extending%20aclocal)
aclocal: configure.in: 382: macro `AM_PATH_GLIB_2_0' not found in library
 <<

Strange,... First off all, I opened synaptic and I saw that 2 versions of Glib were installed. 1.4 and 2.0. I wanted to delete the 1.4 but off corse i couldn't do that because several programs such as xmms would be deleted also because they depend on it (I think). But has this to do anything with the above message? I already opened the website given in the error, but I'm kinda noob at this :biggrin: 

So could someone help me plz.

Greetz Daan

---

### Post by DirtDawg on 2007-01-23
Do you have libglib2.0-dev installed? If not, install it and try again.

---

