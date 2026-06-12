---
title: "can't istall gtk+-2.0.9"
date: 2006-11-12
forum: General Help
---

### Post by yuan314159 on 2006-11-12
I want to play the APE music on ubuntu.And I download bmp-mac-0.1.1.tar.gz.This need to install gtk+-2.0.9.tar.bz2.when i make the 
gtk+-2.0.9.tar.bz2,It says  GLIB 2.0.6 or better is required.
My problem is I have installed  GLIB 2.0.6.Why it still say GLIB 2.0.6 or better is required?


the follows is what the computer says :
checking for GLIB - version >= 2.0.6... 
*** 'pkg-config --modversion glib-2.0' returned 2.0.6, but GLIB (2.12.4)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable
 PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.6 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/).

---

### Post by bhirning on 2006-11-12
i had the same problem with a different program...

the workaroud that i found went something like this

./configure  --without glib check

i know that this will not work as is but this is a start.. i will post the exact command when i find it.

good luck

---

### Post by bhirning on 2006-11-12
it might be this way?

./configure --disable-glibtest

still looking:-k

---

### Post by yopnono on 2006-11-12
Open the configure file and search for the glib, then just change the number to... any lower value.

---

### Post by yuan314159 on 2006-11-17
Thanks  all of you.
     I still can't install the gtk, but I have found other way to solve it. I download the files directly, which the bmp-mac will install  in my system .
 And  I copy them in the /usr.
   Them  everything is solved .

---

