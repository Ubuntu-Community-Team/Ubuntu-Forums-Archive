---
title: "Trying to install GTK+3, problems with GLib"
date: 2012-11-12
forum: General Help
---

### Post by Laize on 2012-11-12
I'm trying to install GTK+3.  To that end I'm compiling everything it needs, but GLib hasn't been making it easy.

The latest one is something I'm having difficulty with and was hoping someone could help me out.

GLib seems to install without a problem.  Then, however, on the $sudo make install of ATK I'm getting the following error.

```
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.31.2... 
*** 'pkg-config --modversion glib-2.0' returned 2.32.4, but GLIB (2.32.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.31.2 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
~/Downloads/atk-2.4.0$ pkg-config --modversion
Must specify package names on the command line
~/Downloads/atk-2.4.0$ pkg-config --modversion glib
Package glib was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib' found

```

The version of glib from the FTP site is most definitely 2.32.4.  That would, logically, mean I have to remove GLib 2.32.3.  Here's where the problem is:  I haven't a single clue where GLib 2.32.3 is.

I found a package in my archives containing that exact version of GLib, but have no idea where it's installed to.  Using dpkg -r does me no good without even knowing the package name either.

---

### Post by AlexDudko on 2012-11-12
Isn't it easier just to execute:
> sudo apt-get install  libgtk-3-0


---

### Post by Laize on 2012-11-12
> **AlexDudko said:**
> Isn't it easier just to execute:

I thought that too, but then I get the following error when trying to install GTK+3

```
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.32.0    atk >= 2.2.0    pango >= 1.30.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.26.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

So I install GLib manually (which goes smooth) and then I install ATK and get this.

```
checking for GLIB - version >= 2.31.2... 
*** 'pkg-config --modversion glib-2.0' returned 2.32.4, but GLIB (2.32.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.31.2 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

---

### Post by AlexDudko on 2012-11-12
What version of Ubuntu are you using? Isn't it an EOL one?
What's the output of
> lsb_release -a

---

### Post by Laize on 2012-11-12
> **AlexDudko said:**
> What version of Ubuntu are you using? Isn't it an EOL one?
What's the output of

Precise.

~$ lsb_release -a```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

---

### Post by AlexDudko on 2012-11-13
Are you sure you are connected to Internet? Do these commands run smoothly?
> sudo apt-get update
sudo apt-get upgrade
What's the output of this command:
> apt-cache search libgtk-3-0

---

### Post by Laize on 2012-11-13
> **AlexDudko said:**
> Are you sure you are connected to Internet? Do these commands run smoothly?

What's the output of this command:

Yes, I'm connected to the Internet.

I run APT updates regularly.  The installation of libgtk-3-0 does nothing for the situation.

---

### Post by Laize on 2012-11-13
pkg-config is correct.  My version of GLib is, indeed, 2.32.4.  Based on the following error message:

```
checking for GLIB - version >= 2.31.2... 
*** 'pkg-config --modversion glib-2.0' returned 2.32.4, but GLIB (2.32.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.31.2 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

I need to uninstall the old version of GLib OR modify my LD_LIBRARY_PATH.  That bit is kind of out of my element.  All that document contains is as follows.

$gedit /etc/ld.so.conf
```
include /etc/ld.so.conf.d/*.conf

```

---

### Post by Laize on 2012-11-13
Well I sort of solved my problem... in a way.

Turns out $ sudo apt-get purge libgtk-3-0 is a bad idea.

Cloned my OS back onto my drive and started over with GTK+3.

New error now.

Running ./config for GTK+3 now produces:

```
checking for XGetEventData... yes
configure: error: *** XInput2 extension not found. Check 'config.log' for more details.

```

Update: Seem to have fixed the problem.

```
$ sudo apt-get install xorg-dev
```

Compiling the package right now.  Remind me to never install Debian if this is what everything is like.

---

### Post by Nybbling on 2013-04-27
So I know that this is an old thread, and OP has probably never looked back, but for those internet denizens who don't have a hard drive image to fall back on:

Go [here]("http://ftp.acc.umu.se/pub/gnome/sources/glib") and download the version of GLib that your error is claiming is actually installed (the older version) and just install it. Even though GLib is a "newer" version -ish, this set my system straight and allowed it to carry on with the GTK install.

---

