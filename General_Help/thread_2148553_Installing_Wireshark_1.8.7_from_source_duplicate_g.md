---
title: "Installing Wireshark 1.8.7 from source: duplicate glib problem."
date: 2013-05-25
forum: General Help
---

### Post by socialismo on 2013-05-25
Hello everyone.

I'm trying to install the latest stable version of Wireshark.


Apparently there is no official ".deb" package to install it. After some dependencies satisfied I can not leave the glib checkpoint.


First, the 'configure' script does not recognized that I already have version 2.34.3 of the library on the system, so I installed 2.36.0 from source. The problem now is that the script recognizes both and need me to choose and set the correct path.

```
*** 'pkg-config --modversion glib-2.0' returned 2.34.3, but GLIB (2.36.0)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: GLib 2.14 or later distribution not found.
```

As suggested, I configured the 'PKG_CONFIG_PATH' and 'LD_LYBRARY_PATH' to '/usr/local/lib/pkgconfig/' and '/usr/lib', respectively, to point to the newest version. No modifications on the behavior.

After reading the installation instructions for Wireshark, I changed the paths to the original value and set 'disable-usr-local' in 'configure' script, but the result was the same.

```
rodrigo@capela:~/Downloads/wireshark-1.8.7$ dpkg -l libglib* | grep ii
ii  libglib-perl                              3:1.261-1                                  i386         interface to the GLib and GObject libraries
ii  libglib2.0-0:i386                         2.36.0-1ubuntu2                            i386         GLib library of C routines
ii  libglib2.0-bin                            2.36.0-1ubuntu2                            i386         Programs for the GLib library
ii  libglib2.0-cil                            2.12.10-5                                  i386         CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                           2.36.0-1ubuntu2                            all          Common files for GLib library
ii  libglib2.0-dev                            2.36.0-1ubuntu2                            i386         Development files for the GLib library
ii  libglibmm-2.4-1c2a:i386                   2.35.9-0ubuntu1                            i386         C++ wrapper for the GLib toolkit (shared libraries)
rodrigo@capela:~/Downloads/wireshark-1.8.7$

```

```
rodrigo@capela:~/Downloads/wireshark-1.8.7$ sudo ldconfig -v | grep glib
/sbin/ldconfig.real: Não foi possível stat /lib/i686-linux-gnu: Arquivo ou diretório não encontrado
/sbin/ldconfig.real: Não foi possível stat /usr/lib/i686-linux-gnu: Arquivo ou diretório não encontrado
/sbin/ldconfig.real: Caminho `/lib/i386-linux-gnu' informado mais de uma vez
/sbin/ldconfig.real: Caminho `/usr/lib/i386-linux-gnu' informado mais de uma vez
    libglib-2.0.so.0 -> libglib-2.0.so.0.3600.0
    libnm-glib-vpn.so.1 -> libnm-glib-vpn.so.1.1.0
    libdbus-glib-1.so.2 -> libdbus-glib-1.so.2.2.2
    libdbusmenu-glib.so.4 -> libdbusmenu-glib.so.4.0.12
    libsignon-glib.so.1 -> libsignon-glib.so.1.0.0
    libaccounts-glib.so.0 -> libaccounts-glib.so.0.1.3
    libpyglib-gi-2.0-python3.3.so.0 -> libpyglib-gi-2.0-python3.3.so.0.0.0
    libglibmm-2.4.so.1 -> libglibmm-2.4.so.1.3.0
    libpackagekit-glib2.so.14 -> libpackagekit-glib2.so.14.0.15
    libpoppler-glib.so.8 -> libpoppler-glib.so.8.4.0
    libglibmm_generate_extra_defs-2.4.so.1 -> libglibmm_generate_extra_defs-2.4.so.1.3.0
    libavahi-glib.so.1 -> libavahi-glib.so.1.0.2
    libjson-glib-1.0.so.0 -> libjson-glib-1.0.so.0.1502.0
    libpulse-mainloop-glib.so.0 -> libpulse-mainloop-glib.so.0.0.4
    libnm-glib.so.4 -> libnm-glib.so.4.5.0
    libpyglib-gi-2.0-python2.7.so.0 -> libpyglib-gi-2.0-python2.7.so.0.0.0
    libtelepathy-glib.so.0 -> libtelepathy-glib.so.0.78.2
    libglib-2.0.so.0 -> libglib-2.0.so.0.3400.3
    libglib-2.0.so.0 -> libglib-2.0.so.0.3400.3
    libpyglib-2.0-python2.7.so.0 -> libpyglib-2.0-python2.7.so.0.0.0
    libupower-glib.so.1 -> libupower-glib.so.1.0.2
rodrigo@capela:~/Downloads/wireshark-1.8.7$

```

I would like to remove the latest version and correctly configure the Ubuntu originally brought me so I can fix the problem and install Wireshark.

Any suggestions?

Thanks in advance.

---

