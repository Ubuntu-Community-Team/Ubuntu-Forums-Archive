---
title: "problem with libtorrent configure"
date: 2007-03-22
forum: General Help
---

### Post by hanjet on 2007-03-22
I seem to have a recurring issue trying to configure libtorrent.
I downloaded the tarball, ran autoconf, then configure.
I got this error:

[I]./configure: line 23467: syntax error near unexpected token `OPENSSL,'
./configure: line 23467: `      PKG_CHECK_MODULES(OPENSSL, openssl,'
[/I]

so i then apt-get installed openssl (it was already installed)

i tried again, got the same error

then i downloaded openssl (the latest tarball) and compiled it manually

i tried again and got a different error about environment variables and pkg-check and openssl_cflags & openssl_libs

so there i was super confused, and decided (for posterity) to try one last time, and all that resulted from that was the same *first* error ([I]./configure: line 23467: syntax error near unexpected token `OPENSSL,'
./configure: line 23467: `      PKG_CHECK_MODULES(OPENSSL, openssl,'
[/I])

that left me looking for help, so here i am

thank you!

EDIT: i tried again this morning, after installing libssl-dev (which my friend told me to do), and i got the same pkg_check_modules error...

---

### Post by zvacet on 2007-03-22
Maybe I´m completly wrong but try 
1. tar xvfz program tar.gz
2. cd /program
3. ./configure
4. make
5. sudo make install

---

