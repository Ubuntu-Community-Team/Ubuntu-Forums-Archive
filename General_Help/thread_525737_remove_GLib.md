---
title: "remove GLib"
date: 2007-08-14
forum: General Help
---

### Post by smith19 on 2007-08-14
Hi there,

I was trying to install GTK+ and it dependency needs atk,pango and glib. i compiled pango successfully also glib2.12.13 but atk1.0 says

*** 'pkg-config --modversion glib-2.0' returned 2.12.13, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH  

ok do you i have to remove Glib and reinstall it again? and how do i remove.
Can you please suggest what step I should take?

Thanks

 
Regards,

smith19

---

### Post by wirelessmonkey on 2007-08-14
Ok, if you really want to do it from scratch, I can help you with that, but it's much much much easier just to apt-get it...
sudo apt-get install libgtk2.0-common libgtk2.0-dev

It will take care of the dependencies for you. In fact you may find that it's already installed.

---

### Post by CPUDave on 2007-08-24
*** 'pkg-config --modversion glib-2.0' returned 2.12.13, but GLIB (2.12.11)
*** was found!

While I am trying to install ATK, I have the same error and the operations suggested did not resolve it.

Somehow, 2.12.11 is registered although I have installed 2.12.13.

Any better suggestions?

---

