---
title: "manual install: how? (trying to install a package from src)"
date: 2007-10-28
forum: General Help
---

### Post by ogwilson on 2007-10-28
well i do this:

```
cd /home/username/Desktop/avant-window-navigator-0.1.1
```

Now, once in there, I do

```
./configure
```

and always, i get this message

```
..
..
..
checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Can anyone help me? what am I doing wrong?

---

### Post by taurus on 2007-10-28
You need both **libgtk** and **libgtk-dev** packages.  So, install those using synaptic first and then build your avant again.  You also need the **build-essential** package if you want to build anything from source.

---

### Post by ogwilson on 2007-10-28
Thanks, i'll try that now and let you know how it goes.

And yea, I read from the guide that i needed build-essential which i now have, but nowhere did it mention libgtk lol. how were you able to figure that out?

---

### Post by ogwilson on 2007-10-28
ok now i get this message:
```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

i notice theres just that one package its asking for instead of all the other ones. i look for it in synaptic, and i see gconf is installed, but im not sure if it's the right one because the name didn't specifically say gconf-2.0

---

### Post by taurus on 2007-10-28
Look for gconf-dev.

---

### Post by ogwilson on 2007-10-28
ok great that did it for ./configure. now what do i do next? I did make then make install, but after make install i got this error:

```
/usr/bin/install: cannot create regular file `/usr/local/bin/avant-window-navigator': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/quentyn/Desktop/avant-window-navigator-0.1.1/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/quentyn/Desktop/avant-window-navigator-0.1.1/src'
make: *** [install-recursive] Error 1

```

EDIT - I didnt get the error anymore after using SUDO. So after all that's done, is it ready to use or are there more steps?

---

### Post by taurus on 2007-10-28
You need to **run make** install with root privilege since you are install it to your system.

```
**sudo** make install
```

p.s.  It's all there for you to use now.

---

### Post by ogwilson on 2007-10-28
Thank you. I think the installation is complete. question though:

1. I restarted X server (CTRL+ALT+BS) and i log back in and it says NAUTILUS CANT BE USED AT THIS TIME DUE TO UNEXPECTED ERROR. But I restarted X server again the same way and everything was fine. Did something happen?

2. After restarting X server the application finally showed up ander the Accessories folder, and its settings under the system/preferences panel, but whenever i click either of them, nothing happens. Is this because of something I did?

---

### Post by ogwilson on 2007-10-28
Please disregard previous post. i noticed i was using an outdated version of the program from the get go. now im trying to install the updated 0.2 and i get this:

```
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

so i check the repos for Python headers, and i install what i think it is i might need, but apparently i'm still getting the same error. And when i search for anything that has to do with python, i get tons of results and i dont know whats what.\

EDIT- Heh, sorry please bare with me. I checked awn's website and got the correct python stuff, now i'm needing these things and neither of them are showing up in the repos

```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found
No package 'libglade-2.0' found
No package 'xdamage' found
No package 'xcomposite' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by ogwilson on 2007-10-28
bump

---

### Post by ogwilson on 2007-10-28
bump please

---

### Post by Thyme on 2007-10-28
Try setting PKG_CONFIG_PATH first: 

If you have a 64-bit processor: export PKG_CONFIG_PATH=/usr/lib64/pkgconfig
If you have a 32-bit processor: export PKG_CONFIG_PATH=/usr/lib/pkgconfig

If this doesn't change anything then you have to install all those packages and their headers. For example:

xcomposite:

1. libxcomposite1
2. libxcomposite-dev

libgnome-2.0:

1. libgnome-dev

gnome-desktop-2.0:

1. gnome-desktop-data
2. libgnome-desktop-2
3. libgnome-desktop-dev 

gnome-fvs-2.0

1. libgnomevfs2-0
2. libgnomevfs2-bin
3. libgnomevfs2-common
4. libgnomevfs2-dev
5. libgnomevfs2-extra

You can just copy and past the packages you need and search for it .. Good luck :)

---

### Post by ogwilson on 2007-10-28
thanks ill definitely try that. i dont get how they say you need one thing, but the packages are named something completely different. i think it'd be easier on users like me if they were at least more descriptive?

---

### Post by ogwilson on 2007-10-28
ok now its saying im missing this package.

```
No package 'dbus-glib-1' found

```

but the other ones in my previous post seems to be installed now. so do i just search for dbus or glib or something?

---

### Post by ogwilson on 2007-10-28
ok, i got the application installed (FINALLY) lol thanks for the help guys. now time to find out why it wont launch, which is out of your hands. thanks for all the help!

---

### Post by larryfroot on 2007-10-28
ha crossed posts! Glad you got it sorted anyways...

---

### Post by ogwilson on 2007-10-28
heh are you from the official awn forums?

---

