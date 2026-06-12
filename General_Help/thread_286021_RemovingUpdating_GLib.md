---
title: "Removing/Updating GLib"
date: 2006-10-27
forum: General Help
---

### Post by orsula on 2006-10-27
Hi,
I am trying to install a package from source that requires glib >= 2.12.0. I downloaded glib-2.12.3 and installed succesfully in /usr/local/. However, when I run ./configure on the apckage I need to install, I get the following error message:
```
checking for GLIB - version >= 2.12.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.3, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

My question is, how do I remove the older version GLIB(2.10.3) in order for ./configure to recognize the new version? Should I keep th eolder version and change some environment variable? If so , how do I do that? I tried to follow the instruction by adding the path /usr/local/glib_2.12.3 to the file /etc/ld.so.conf and then running ```
ldconfig
``` but that didn't help.

Any ideas?
Thank you very much
Gideon

---

### Post by orsula on 2006-10-27
I forgot to mentioned that what I am trying to install is Gwyddion. Asoftware for viewing and manipulating images from Atomic Force Microscopes. (@ [HTML]http://gwyddion.net/[/HTML]). Also, when I run ldconfig, I actually run ```
sudo ldcofig
```

Thanks again,
Gideon

---

### Post by skymt on 2006-10-27
A lot of packages in Dapper rely on GLib 2.10. Your best bet is to upgrade to Edgy, which has 2.12.

---

### Post by yeti-dn on 2006-11-17
If the thing you are trying to install is Gwyddion, any GLib and Gtk+ versions from 2.6 above will do.  You definitely do not need GLib 2.12.

---

### Post by howlingmadhowie on 2006-12-08
hi everybody, i'm also trying to install gwyddion, get stuck with the following text, however:

checking for pangoft2 gtk+-2.0 >= 2.6.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found


and then it stops. i've tried installing every package i could find that mentioned gtk+2.0 and it hasn't helped. it's probably a pretty easy problem. anybody know a solution?

---

### Post by Sef on 2006-12-27
I wonder if there is a bug in Edgy with GLIB.    I am having the same problem except I am trying to update GAIM to 2.0.0beta5.

---

### Post by saphil on 2007-04-15
I am considering the other side of this - say you already had glib2.12.4 and installed 2.12.9 (or 2.13.0) having not realized there was a $PATH= problem in the mix...  how do I back the newer version out?  glib supports about 75 gui packages in edgy.  I am almost positive it will kill the gui to remove libglib-2.12.4 using apt-get or synaptic.  

I am attempting to install Labyrinth mind-mapper on a new edgy box.  It is part of the repos for Feisty and worked well there.  I installed it on Dapper (when the current feisty box was a dapper pre-beta)  but I can't remember having problems then.

---

