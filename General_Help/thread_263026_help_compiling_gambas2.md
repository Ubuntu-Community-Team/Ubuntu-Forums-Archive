---
title: "help compiling gambas2"
date: 2006-09-22
forum: General Help
---

### Post by mebarg on 2006-09-22
hi i need help compiling gambas 1.9.42
i get this after ./configure
THESE COMPONENTS ARE DISABLED:

- gb.corba
- gb.db.firebird
- gb.db.odbc
- gb.db.sqlite2
- gb.db.sqlite3
- gb.net.curl
- gb.pdf
- gb.sdl

how i can fix this?
wath pakages do i need?
tanks

bye

---

### Post by Perfect Storm on 2006-09-23
Make sure you have -dev packages of the specific application installed.
Some of the stuff you might to enable when running ./configure.
Try to run ./configure --help it usually list what to add/remove.

---

