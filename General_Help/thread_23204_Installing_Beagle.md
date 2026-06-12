---
title: "Installing Beagle"
date: 2005-03-31
forum: General Help
---

### Post by timelord726 on 2005-03-31
I'm trying to install Beagle.  I was advancing alright, but then I did something (I'm not sure what) and I can't get back.  Here's my output:

```
danny@danny-ubuntu:~$ sudo apt-get install mono libmono-dev mono-gac  libevolution-cil libgtksourceview-cil \
> libgecko-cil libdbus-cil libgconf-cil libgnomeui-dev libxss-dev gtk-doc-tools gtk-sharp-gapi sqlite \
> automake1.8 cvs libtool libglade-cil libglib-cil libgmime-cil libgnome-cil libgtk-cil \
> dbus-1-dev dbus-glib-1-dev gcc g++ mozilla-dev libgtk2.0-dev libexif-dev libsqlite0-dev libexif-dev
Reading package lists... Done
Building dependency tree... Done
libmono-dev is already the newest version.
libgnomeui-dev is already the newest version.
libxss-dev is already the newest version.
gtk-doc-tools is already the newest version.
sqlite is already the newest version.
automake1.8 is already the newest version.
cvs is already the newest version.
libtool is already the newest version.
dbus-1-dev is already the newest version.
dbus-glib-1-dev is already the newest version.
gcc is already the newest version.
g++ is already the newest version.
mozilla-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libexif-dev is already the newest version.
libsqlite0-dev is already the newest version.
libexif-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk-sharp-gapi: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                           mono-mint (>= 1.0.5) but it is not going to be installed
                  Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libdbus-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                        mono-mint (>= 1.0.5) but it is not going to be installed               Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libevolution-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                             mono-mint (>= 1.0.5) but it is not going to be installed
                    Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgconf-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                         mono-mint (>= 1.0.5) but it is not going to be installed
                Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgecko-cil: Depends: mono-jit (>= 1.0.4) but it is not going to be installed or
                         mono-mint (>= 1.0.4) but it is not going to be installed
                Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libglade-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                         mono-mint (>= 1.0.5) but it is not going to be installed
                Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libglib-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                        mono-mint (>= 1.0.5) but it is not going to be installed               Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgmime-cil: Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgnome-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                         mono-mint (>= 1.0.5) but it is not going to be installed
                Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgtk-cil: Depends: mono-jit (>= 1.0.5) but it is not going to be installed or
                       mono-mint (>= 1.0.5) but it is not going to be installed
              Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  libgtksourceview-cil: Depends: mono-jit (>= 1.0.4) but it is not going to be installed or
                                 mono-mint (>= 1.0.4) but it is not going to be installed
                        Depends: mono-assemblies-base (>= 1.0) but it is not going to be installed
  mono: Depends: mono-jit (= 1.0.5-1) but it is not going to be installed or
                 mono-mint (= 1.0.5-1) but it is not going to be installed
        Depends: mono-utils (= 1.0.5-1) but it is not going to be installed
        Depends: mono-assemblies-arch but it is not going to be installed
  mono-gac: Depends: mono-assemblies-base but it is not going to be installed
E: Broken packages
```

---

### Post by bored2k on 2005-03-31
What guide are you using ?

I used [http://www.beaglewiki.org/index.php/UbuntuInstall](http://www.beaglewiki.org/index.php/UbuntuInstall) and it went smooth .

[SIZE=1]after installing it, I decided to stick with non-gui locate btw [that beagle daemon is a bit of a resource hog @ times] .[/SIZE]

---

### Post by timelord726 on 2005-04-01
I'm using the guide for Hoary on the Ubuntu site.

---

