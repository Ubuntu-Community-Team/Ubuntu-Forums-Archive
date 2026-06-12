---
title: "synce error when building"
date: 2007-05-25
forum: General Help
---

### Post by adwatkin19 on 2007-05-25
I have downloaded synce from the website, the latest 0.10.0 version for wm5. i have extracted the files and when i come to run the following command:

./configure --enable-desktop-integration

it scrolls loads of things on the screen then gives me this error at the end of it all:

configure: error: desktop integration requested but D-Bus could not be found

does anyone know what causes this, i have checked on the synaptic for all DBus items, and nothing seems to be missing, but im not sure what i should have installed.

anyone that can shed some light on this for me with my saviour

thanks alot

adwatkin19

---

### Post by wersdaluv on 2007-05-27
I have good news!

[http://www.nabble.com/Re:-SynCE-0.10.0-Debian-Packages-t3780467.html](http://www.nabble.com/Re:-SynCE-0.10.0-Debian-Packages-t3780467.html)

> Add the following lines to your /etc/apt/sources.list:

deb [http://jonnylamb.com](http://jonnylamb.com) debian/
deb-src [http://jonnylamb.com](http://jonnylamb.com) debian/

---

### Post by Brocco on 2007-05-27
```
$ sudo aptitude install libdbus-glib-1-dev
```

I figured this out by searching for packages with "dbus" and "dev" in their names.  Packages with "-dev" are used for compiling programs.

Cheers,
Brocco

---

