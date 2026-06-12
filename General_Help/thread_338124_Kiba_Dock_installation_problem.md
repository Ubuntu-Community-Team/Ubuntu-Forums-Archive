---
title: "Kiba Dock installation problem"
date: 2007-01-14
forum: General Help
---

### Post by vd853 on 2007-01-14
I followed the tutorial, but can't get pass it.

[http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)

```
viluan@viluan-laptop:~$ sudo aptitude remove automake1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
viluan@viluan-laptop:~$ sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libgtop2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "checkinstall"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
viluan@viluan-laptop:~$  cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/viluan/.cvspass does not exist - creating a new file
cvs checkout: Updating kiba-dock
U kiba-dock/AUTHORS
U kiba-dock/COPYING
U kiba-dock/ChangeLog
U kiba-dock/Makefile.am
U kiba-dock/NEWS
U kiba-dock/README
U kiba-dock/TODO
U kiba-dock/autogen.sh
U kiba-dock/configure.in
U kiba-dock/kiba-dock.pc.in
cvs checkout: Updating kiba-dock/akamaru
U kiba-dock/akamaru/Makefile.am
U kiba-dock/akamaru/akamaru.c
U kiba-dock/akamaru/akamaru.h
U kiba-dock/akamaru/main.c
cvs checkout: Updating kiba-dock/bin
cvs checkout: Updating kiba-dock/dock
U kiba-dock/dock/Makefile.am
U kiba-dock/dock/kiba-akamaru.c
U kiba-dock/dock/kiba-akamaru.h
U kiba-dock/dock/kiba-dock.c
U kiba-dock/dock/kiba-dock.h
U kiba-dock/dock/kiba-events.c
U kiba-dock/dock/kiba-events.h
U kiba-dock/dock/kiba-gconf.c
U kiba-dock/dock/kiba-gconf.h
U kiba-dock/dock/kiba-geometry.c
U kiba-dock/dock/kiba-geometry.h
U kiba-dock/dock/kiba-object.c
U kiba-dock/dock/kiba-object.h
U kiba-dock/dock/kiba-render.c
U kiba-dock/dock/kiba-render.h
cvs checkout: Updating kiba-dock/files
U kiba-dock/files/Makefile.am
U kiba-dock/files/SimpleGladeApp.py
U kiba-dock/files/kiba.schemas
cvs checkout: Updating kiba-dock/gset-kiba
U kiba-dock/gset-kiba/Makefile.am
U kiba-dock/gset-kiba/gset-kiba.c
U kiba-dock/gset-kiba/gset-kiba.glade
cvs checkout: Updating kiba-dock/icons
U kiba-dock/icons/Makefile.am
U kiba-dock/icons/kiba_128.png
U kiba-dock/icons/kiba_16.png
U kiba-dock/icons/kiba_24.png
U kiba-dock/icons/kiba_48.png
U kiba-dock/icons/kiba_64.png
cvs checkout: Updating kiba-dock/plugins
U kiba-dock/plugins/Makefile.am
U kiba-dock/plugins/clock.c
U kiba-dock/plugins/launcher.c
U kiba-dock/plugins/memory.c
U kiba-dock/plugins/taskbar.c
cvs checkout: Updating kiba-dock/utils
U kiba-dock/utils/Makefile.am
U kiba-dock/utils/kiba-icon-editor.py
U kiba-dock/utils/kiba-icons.glade
U kiba-dock/utils/kiba-systray.py
U kiba-dock/utils/populate-dock.sh
viluan@viluan-laptop:~$ cd kiba-dock
viluan@viluan-laptop:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: configure.in: creating directory config
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
viluan@viluan-laptop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
viluan@viluan-laptop:~/kiba-dock$ 

```

---

### Post by ZaYeR on 2007-01-15
You must install libtool ... it's writen in thread you linked: [http://www.ubuntuforums.org/showthread.php?t=268645]("http://www.ubuntuforums.org/showthread.php?t=268645")

---

### Post by Gonzo_Dark on 2007-02-19
> **vd853 said:**
> I followed the tutorial, but can't get pass it.

[http://ubuntuforums.org/showthread.php?t=268645](http://ubuntuforums.org/showthread.php?t=268645)

```
viluan@viluan-laptop:~$ sudo aptitude remove automake1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
viluan@viluan-laptop:~$ sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libgtop2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "checkinstall"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
viluan@viluan-laptop:~$  cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cvs checkout: CVS password file /home/viluan/.cvspass does not exist - creating a new file
cvs checkout: Updating kiba-dock
U kiba-dock/AUTHORS
U kiba-dock/COPYING
U kiba-dock/ChangeLog
U kiba-dock/Makefile.am
U kiba-dock/NEWS
U kiba-dock/README
U kiba-dock/TODO
U kiba-dock/autogen.sh
U kiba-dock/configure.in
U kiba-dock/kiba-dock.pc.in
cvs checkout: Updating kiba-dock/akamaru
U kiba-dock/akamaru/Makefile.am
U kiba-dock/akamaru/akamaru.c
U kiba-dock/akamaru/akamaru.h
U kiba-dock/akamaru/main.c
cvs checkout: Updating kiba-dock/bin
cvs checkout: Updating kiba-dock/dock
U kiba-dock/dock/Makefile.am
U kiba-dock/dock/kiba-akamaru.c
U kiba-dock/dock/kiba-akamaru.h
U kiba-dock/dock/kiba-dock.c
U kiba-dock/dock/kiba-dock.h
U kiba-dock/dock/kiba-events.c
U kiba-dock/dock/kiba-events.h
U kiba-dock/dock/kiba-gconf.c
U kiba-dock/dock/kiba-gconf.h
U kiba-dock/dock/kiba-geometry.c
U kiba-dock/dock/kiba-geometry.h
U kiba-dock/dock/kiba-object.c
U kiba-dock/dock/kiba-object.h
U kiba-dock/dock/kiba-render.c
U kiba-dock/dock/kiba-render.h
cvs checkout: Updating kiba-dock/files
U kiba-dock/files/Makefile.am
U kiba-dock/files/SimpleGladeApp.py
U kiba-dock/files/kiba.schemas
cvs checkout: Updating kiba-dock/gset-kiba
U kiba-dock/gset-kiba/Makefile.am
U kiba-dock/gset-kiba/gset-kiba.c
U kiba-dock/gset-kiba/gset-kiba.glade
cvs checkout: Updating kiba-dock/icons
U kiba-dock/icons/Makefile.am
U kiba-dock/icons/kiba_128.png
U kiba-dock/icons/kiba_16.png
U kiba-dock/icons/kiba_24.png
U kiba-dock/icons/kiba_48.png
U kiba-dock/icons/kiba_64.png
cvs checkout: Updating kiba-dock/plugins
U kiba-dock/plugins/Makefile.am
U kiba-dock/plugins/clock.c
U kiba-dock/plugins/launcher.c
U kiba-dock/plugins/memory.c
U kiba-dock/plugins/taskbar.c
cvs checkout: Updating kiba-dock/utils
U kiba-dock/utils/Makefile.am
U kiba-dock/utils/kiba-icon-editor.py
U kiba-dock/utils/kiba-icons.glade
U kiba-dock/utils/kiba-systray.py
U kiba-dock/utils/populate-dock.sh
viluan@viluan-laptop:~$ cd kiba-dock
viluan@viluan-laptop:~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: configure.in: creating directory config
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:30: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
viluan@viluan-laptop:~/kiba-dock$ make
make: *** No targets specified and no makefile found.  Stop.
viluan@viluan-laptop:~/kiba-dock$ 

```

You need to install libtool ;)

open your terminal and press :

su
your password
yum install libtool

hope it helps ;)

// Gonzo_Dark

---

### Post by ramjet_1953 on 2007-02-19
Have you tries KoolDock?

Far less painful. 

Works in both GNOME and KDE, is very easy to set-up and add icons to.

It also has a nice auto-hide feature.

Regards,
Roger :cool:

---

