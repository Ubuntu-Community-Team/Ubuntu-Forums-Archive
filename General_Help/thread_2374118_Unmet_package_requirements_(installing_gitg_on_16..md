---
title: "Unmet package requirements (installing gitg on 16.04)"
date: 2017-10-12
forum: General Help
---

### Post by UTAN_dev on 2017-10-12
On Ubuntu 16.04.1 LTS I'm trying to install a newer version of gitg  (3.26) than provided by apt (3.17). I downloaded the archive and  followed the instructions, and need to install a bunch of dependencies. Here's the end of the output from `./configure` :
```
checking for sinf in -lm... yes
checking for native Win32... no
checking for LIBGITG... no
configure: error: Package requirements (
    gthread-2.0 >= 2.38
    glib-2.0 >= 2.38
    gobject-2.0 >= 2.38
    gmodule-2.0 >= 2.38
    gio-2.0 >= 2.38
    gio-unix-2.0 >= 2.38
    gobject-introspection-1.0 >= 0.10.1
    libgit2-glib-1.0 >= 0.25.0
    libgit2-glib-1.0 < 0.27.0
    gtk+-3.0 >= 3.20.0
    gtksourceview-3.0 >= 3.10
    gsettings-desktop-schemas
    gee-0.8
    libsoup-2.4
    libsecret-1
) were not met:

Requested 'libgit2-glib-1.0 >= 0.25.0' but version of libgit2-glib is 0.24.0
Requested 'gtk+-3.0 >= 3.20.0' but version of GTK+ is 3.18.9

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGITG_CFLAGS
and LIBGITG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

So I tried installing a new version of libgit2-glib:

```
$ sudo apt-get install libgit2-glib-1.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgit2-glib-1.0-dev is already the newest version (0.24.0-3).
The following packages were automatically installed and are no longer required:
  libmircommon5 libwacom-bin snap-confine ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 105 not upgraded.
```

Being fairly green, I don't know what to do at this point. Thanks for your help.

Oh, in case you're asking about my sources file:

```
$ cat /etc/apt/sources.list 
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
```

---

### Post by Perfect Storm on 2017-10-13
> Requested 'libgit2-glib-1.0 >= 0.25.0' but version of libgit2-glib is 0.24.0
Requested 'gtk+-3.0 >= 3.20.0' but version of GTK+ is 3.18.9

Ubuntu 16.04 have the libs but they are too old. It may require that you upgrade ubuntu if you want it to work.

---

