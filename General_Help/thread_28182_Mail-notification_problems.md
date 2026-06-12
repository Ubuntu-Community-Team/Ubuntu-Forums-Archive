---
title: "Mail-notification problems"
date: 2005-04-19
forum: General Help
---

### Post by wowtip on 2005-04-19
I am currently trying to get mail-notification ([http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)) working with SSL enabled. Not an easy task.

**First try: The package in the repositories:**

```
apt-cache show mail-notification

Package: mail-notification
Priority: optional
Section: universe/gnome
Installed-Size: 1116
Maintainer: Pascal Giard <evilynux@yahoo.com>
Architecture: i386
Version: 1.0-1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libeel2-2 (>= 2.9.1), libgail-common (>= 1.6.6), libgail17 (>= 1.6.6), libgconf2-4 (>= 2.7.3.1), libglade2-0 (>= 1:2.3.6), libglib2.0-0 (>= 2.6.0), libgmime2.1, libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.1), libgnutls11 (>= 1.0.16), libgtk2.0-0 (>= 2.5.6), libice6 | xlibs (>> 4.1.0), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.0), libpopt0 (>= 1.7), libsasl2 (>= 2.1.19), libsm6 | xlibs (>> 4.1.0), libsoup2.2-7 (>= 2.2.1), libx11-6 | xlibs (>> 4.1.0), libxml2 (>= 2.6.11), zlib1g (>= 1:1.2.1), debconf (>= 0.5) | debconf-2.0, gconf2 (>= 2.6.2-1)
Filename: pool/universe/m/mail-notification/mail-notification_1.0-1_i386.deb

```

But that package obviously doesn't have OpenSSL linked at compilation.

**Second try: The .deb package:**

Now i downloaded and installed the .deb package at [http://savannah.nongnu.org/download/mailnotify/](http://savannah.nongnu.org/download/mailnotify/)

([http://savannah.nongnu.org/download/mailnotify/mail-notification_1.0-1_i386.deb](http://savannah.nongnu.org/download/mailnotify/mail-notification_1.0-1_i386.deb))

This package actually works as intended, with SSL enabled. But then another quite annoying problem appears: The Ubuntu Update Manager thinks that I have an obsolete version and nags about it.

This version would work very well for me if there was a way of disabling update manager's checking for new mail-notification updates, but that is not possible as far as I can tell?

**Third try: compiling from source:**

[http://savannah.nongnu.org/download/mailnotify/mail-notification-1.1.tar.gz](http://savannah.nongnu.org/download/mailnotify/mail-notification-1.1.tar.gz)

```

...

2. Instructions

        Mail Notification uses the well-known GNU build system. Hence,
        the following usual sequence will probably satisfy most users:

                $ ./configure --prefix=/usr
                $ make
                <get root privileges, if needed>
                $ make install

        IMPORTANT:

                * You must install Mail Notification in the same
                  prefix as GNOME (commonly /usr or /opt/gnome). To
                  know where GNOME is installed on your system, type:

                        $ pkg-config --variable prefix libgnome-2.0

                * Due to a bug in bonobo-activation
                  (http://bugzilla.gnome.org/show_bug.cgi?id=151082),
                  your session must be restarted after installing Mail
                  Notification.

        The ./configure script options are documented below. They are
        enabled by default and automatically disabled if a requirement
        is not met, so you probably do not need to use them.
...

```

Ok, "pkg-config --variable prefix libgnome-2.0" doesn't produce anything here, should I be worried?

Trying anyway...  $./configure

```

...
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: unable to find the GTK+ library

```

Ok, I am at a loss. GTK+ >= 2.4.0 is installed, but not where ./configure would expect it to be... would be my uninformed guess.



I am running out of ideas, any tips on how to get mail-notification working **with** SSL, but **without** having to live with a nagging Update Manager?

---

### Post by nocturn on 2005-04-20
Do you have the gtk development libraries installed?

---

### Post by wowtip on 2005-04-20
[QUOTE=nocturn]Do you have the gtk development libraries installed?[/QUOTE]
Thanks, that (and a couple of other missing dev libs) was the problem. Now 1.1 runs perfectly.  :D

---

