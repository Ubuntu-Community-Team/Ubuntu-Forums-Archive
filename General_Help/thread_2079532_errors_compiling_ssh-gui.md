---
title: "errors compiling ssh-gui"
date: 2012-11-02
forum: General Help
---

### Post by neutron68 on 2012-11-02
I'm trying to compile ssh-gui in Mythbuntu 11.04.  
see [http://sourceforge.net/projects/ssh-gui/](http://sourceforge.net/projects/ssh-gui/)

I downloaded and uncompressed the source files.  When I tried to MAKE, I got the following:
```
user@Mythbuntu8:~/ssh-gui-0.7.1$ make
gcc -Wall `gtk-config --cflags` `glib-config --cflags` -DPACKAGE="ssh-gui" -DVERSION="0.5"   -c -o ssh-gui.o ssh-gui.c
/bin/sh: gtk-config: not found
/bin/sh: glib-config: not found
ssh-gui.c:1:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
make: *** [ssh-gui.o] Error 1
```
Any idea how I can get gtk-config and glib-config?

Eric

---

### Post by WyleECoyote on 2012-11-02
try this link, you need to install gtk1, it is no longer supported in the repo

[http://askubuntu.com/questions/27994/installing-gtk-config-and-or-fsv-missing-gtk-dependencies](http://askubuntu.com/questions/27994/installing-gtk-config-and-or-fsv-missing-gtk-dependencies)

hope it helps

---

### Post by neutron68 on 2012-11-04
That looks pretty relevant and promising.  Thank you!

Eric

---

