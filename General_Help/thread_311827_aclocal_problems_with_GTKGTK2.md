---
title: "aclocal problems with GTK/GTK2"
date: 2006-12-03
forum: General Help
---

### Post by cogvos on 2006-12-03
Dear all,
First post on main forum so sorry if this the wrong place to put a compile question.

Am trying to build a package called sheepshaver which uses automake.

Took a while to get as far as I am as the default Umbuntu (edgy) install misses out the development libs. Anyway have now run into a problem with gtk.

According to the package installer the gtk development libs are there, but when I type whereis gtk I draw a blank.
At the very start of the output from ./autogen.sh I get 3 warnings

Macro AM_PATH_GTK_2.0 not found in library
Macro AM_PATH_GTK not found in library
Macro AM_PATH_ESD not found in library

Not really bothered about ESD as I have ASLA in the X server. Problem is that the make then bombs lower down with a syntax error right after it searches for AM_PATH_GTK. 

I'm guessing that I still need some gtk libs, but don't know what. What packages do I need to complile an app that uses gtk?

Or do I need to extend aclocal manually? Don't know how to do this.

Any ideas?

John.

---

### Post by dbw on 2007-01-06
Same issue:  while installing e17 from CVS I get the following error:

```
Running aclocal...
aclocal: configure.in: 80: macro `AM_PATH_GTK' not found in library
```

I am running 64bit Edgy Xubuntu.

---

### Post by www.rzr.online.fr on 2007-08-09
I fixed this by installing libgtk1.2-dev
  [http://forums.debian.net/viewtopic.php?p=92754#92754](http://forums.debian.net/viewtopic.php?p=92754#92754)

--
[http://rzr.online.fr/q/tool](http://rzr.online.fr/q/tool)

---

