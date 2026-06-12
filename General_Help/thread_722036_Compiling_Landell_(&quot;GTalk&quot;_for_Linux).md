---
title: "Compiling Landell (&quot;GTalk&quot; for Linux)"
date: 2008-03-12
forum: General Help
---

### Post by Ububurns on 2008-03-12
I have managed to compile all of the obscure dependencies for "Landell", part of the Tapioca project.

However, compiling Landell itself produces an error which I seem to be unable to avoid:

*g++: @MOZILLADEPS_CFLAGS@: No such file or directory*

After this point, everything falls down (ie: no such file and directory, leading to exit):

[I]jscallglue.cpp:35:25: error: gtkmozembed.h: No such file or directory
jscallglue.cpp:36:34: error: gtkmozembed_internal.h: No such file or directory
jscallglue.cpp:38:22: error: nsCOMPtr.h: No such file or directory
[/I]
etc.

However all of these files are installed, as part of firefox-dev.  Might I need to manually specify a directory?

Many thanks.

---

### Post by chelala on 2008-05-19
Same happens to me, any solution yet ?

---

### Post by chelala on 2008-05-19
I saw something and creating a symlink named /usr/include/firefox-2 to /usr/include/firefox makes ti compile a little further

error now is /usr/bin/ld: cannot find -lgtkembedmoz

---

### Post by chelala on 2008-05-19
same goes to the firefox directory on /usr/lib/firefox --> /usr/lib/firefox-2

and finally also install libmono-cairo2.0-cil

all worked OK !

---

### Post by ryanhaigh on 2008-05-20
Are you saying that you managed to get this software to install and run? If so I (and I am sure many others) would be very interested to know exactly what you had to do to get it to work.

---

### Post by chelala on 2008-05-21
well I checked out from like in [http://tapioca-voip.sourceforge.net/wiki/index.php/Landell](http://tapioca-voip.sourceforge.net/wiki/index.php/Landell)

for each proejct to be compiled I had to sinatll some -dev or cil project whish soled the dependency, but I remember for the last one, I had to install firefox-dev, firefox-3.0-dev, firefox-2-dev, then rename as I explained before

I also could mannage to compile and run ereseva directly from google subversion

now though landell runs, it shows a few errors, once you have it compiled we can work togther on makeing it work completely OK

---

