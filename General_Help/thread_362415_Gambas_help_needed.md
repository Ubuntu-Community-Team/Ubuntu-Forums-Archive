---
title: "Gambas help needed"
date: 2007-02-15
forum: General Help
---

### Post by lemmy999 on 2007-02-15
I am trying to compile a dev version of gambas ( can't use the one in the repos for various reasons) I have installed the necessary dev versions of X11, QT3, KDE3, PostgreSQL, MySQL and also gcc libc6 libc6-dev cpp g++.

Compile has failed with  the following error messages

> configure: WARNING: libX11 not found. Check 'config.log' for more details.
checking for XShmAttach in -lXext... (cached) no
configure: WARNING: libXext not found. Check 'config.log' for more details.
checking for QT meta-object compiler... no
configure: error: QT moc compiler not found. Try --with-moc option.
configure: error: /bin/bash './configure' failed for gb.qt

Where do i go next??

---

### Post by po0f on 2007-02-15
lemmy999,

Try installing 'xorg-dev'.  I don't know about the "QT moc compiler not found" error you are getting though.

---

### Post by lemmy999 on 2007-02-15
Poof

Went with your suggestion- no joy!!

Where will i find the "config.log" referred to?

---

### Post by po0f on 2007-02-15
lemmy999,

It should be in the source directory of Gambas.  Post it if you think it'll help.

---

### Post by lemmy999 on 2007-02-15
The config log is probably too big to post but having looked at it the most interesting thing is the following

> ACLOCAL='${SHELL} /home/chris/gambas2-1.9.47/missing --run aclocal-1.9'
AMTAR='${SHELL} /home/chris/gambas2-1.9.47/missing --run tar'
AUTOCONF='${SHELL} /home/chris/gambas2-1.9.47/missing --run autoconf'
AUTOHEADER='${SHELL} /home/chris/gambas2-1.9.47/missing --run autoheader'
AUTOMAKE='${SHELL} /home/chris/gambas2-1.9.47/missing --run automake-1.9'

Is that any use?

---

### Post by lemmy999 on 2007-02-15
Installed various libqt packages and it appaers to have worked!! Now I am getting the following at the end of configure

> THESE COMPONENTS ARE DISABLED:

- gb.compress.bzlib2
- gb.corba
- gb.db.firebird
- gb.db.mysql
- gb.db.odbc
- gb.db.sqlite2
- gb.db.sqlite3
- gb.gtk
- gb.gtk.svg
- gb.ldap
- gb.net.curl
- gb.pcre
- gb.pdf
- gb.qt
- gb.qt.kde
- gb.qte
- gb.sdl
- gb.sdl.sound
- gb.xml


Does this matter ? If so what do i need to do next?

---

### Post by po0f on 2007-02-15
lemmy999,

I'm guessing that those are modules for use with Gambas that have not been built.  Usually when building a program from source, you can specify what optional parts beyond basic funstionality you want to build when you run the configure script.  `./configure --help` from the source directory should give you an idea of what you can enable/disable.

---

