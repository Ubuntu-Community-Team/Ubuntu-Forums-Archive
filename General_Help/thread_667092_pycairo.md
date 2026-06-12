---
title: "pycairo"
date: 2008-01-14
forum: General Help
---

### Post by NuNn DaDdY on 2008-01-14
I recently downloaded AWN, however when I attempt to run the "./configure" file I receive the following message:


No package 'pycairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


I have already ran the apt-get for the necessary files I believe but for some reason it is still not working

---

### Post by articpenguin on 2008-01-14
did you install the pycairo dev packages? dev packages are needed to compile programs. like i need pidgin-dev to compile plugins for pidgin.

---

### Post by NuNn DaDdY on 2008-01-14
I just tried:

sudo apt-get install pycairo-dev 

But it said it couldn't find the necessary file.  What would the command be for the development files for that?  Also, where can I go to find out information on the files I need to have using apt-get?

---

### Post by articpenguin on 2008-01-14
try
> sudo apt-get install python-cairo-dev

---

### Post by NuNn DaDdY on 2008-01-14
Alrighty I got that now but when I run the ./configure file now I receive:

checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.14.1)
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gconf-2.0' found
No package 'dbus-glib-1' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

---

### Post by articpenguin on 2008-01-14
install the devs for those packages. I dont have the time to find them right now. you search for them in synaptic. Like libgnome-dev or something.

---

### Post by articpenguin on 2008-01-14
did you look for awn in the repos?

if your looking for avant-window-manager do

> sudo apt-get install avant-window-navigator

---

### Post by NuNn DaDdY on 2008-01-14
I added the repository's to synaptic and then once I mark Avant Window Manager for installation I receive:

avant-window-navigator-bzr:
 Depends: libawn-bzr but it is not going to be installed
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: libawn-bzr but it is not going to be installed

---

### Post by bwtranch on 2008-01-14
Do you have build-essential installed? That usually solves a lot of things. There are some more things that are useful, too. See the Debian Maintainer's Guide.

---

### Post by PeterJS on 2008-01-14
AWN is isn't in the standard repositories, but there is a copy over on Get Deb.net
[Linky Linky](http://www.getdeb.net/search.php?keywords=awn)

---

