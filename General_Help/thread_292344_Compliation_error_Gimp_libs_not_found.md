---
title: "Compliation error: Gimp libs not found"
date: 2006-11-03
forum: General Help
---

### Post by Tauceti38 on 2006-11-03
I've been trying to compile a plugin for the Gimp, but I keep getting the following error message, no matter what I try. I have the most recent version of the Gimp from the repos, gimp 2.2.13.

The plugin's web site can be found [here]("http://nifelheim.dyndns.org/~cocidius/normalmap/").

```
gcc -c -O3 -Wall `pkg-config --cflags gtk+-2.0 gtkglext-1.0 gimp-2.0` normalmap.c
Package gimp-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gimp-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gimp-2.0' found
normalmap.c:26:21: error: gtk/gtk.h: No such file or directory
normalmap.c:28:26: error: libgimp/gimp.h: No such file or directory
normalmap.c:29:28: error: libgimp/gimpui.h: No such file or directory

```

There are many more lines following this error, but they all come from not knowing the correct directory for gimp. This error occurs as soon as I type "make". There is no .configure file provided, just a make file. I have read comments from people who have this plugin working with the most recent version of gimp, so it certainly can be compiled for gimp 2.2.13.

I was getting a similar error for gtkglext-1.0, which I fixed by installing the dev package for gtkglext, unfortunatly I don't see any dev packages for gimp.

I tried researching pkg-config some, but couldn't find much information about how to fix this, other than installing dev packages and adding the appropriate paths to /etc/ld.so.conf and running ldconfig. I tried both of these, but neither worked. I believe I found the gimp libs in /usr/lib/gimp/2.0, and I added /usr/lib to /etc/ld.so.conf. Could I have the wrong directory? I've tried searching for all the gimp files, but haven't managed to get the search working for anything outside of my home directory.

I'd appreciate any suggestions, thanks.

---

### Post by public_void on 2006-11-03
Looks like your missing libgimp2.0-dev from the repos. Installing that should fix the error messages.

---

### Post by Tauceti38 on 2006-11-03
Thanks a bunch, that fixed it.

---

