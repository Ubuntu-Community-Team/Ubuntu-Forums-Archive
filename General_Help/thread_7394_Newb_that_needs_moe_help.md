---
title: "Newb that needs moe help"
date: 2004-12-06
forum: General Help
---

### Post by Darkenbay on 2004-12-06
ok here is the situation im trying to install naim but keep running into the same error it keeps saying no acceptable c compiler.

here is the log

darkendbay@darkendbay:~/naim-0.11.7.2 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking whether to enable /detach... no, re-run ./configure with --enable-detach
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for Cygwin... no


Configuring C compiler

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

any help would be apperciated

---

### Post by Hikaru79 on 2004-12-06
Do this first:

```

sudo apt-get install build-essential

```

Then try your line again :)

---

### Post by Darkenbay on 2004-12-06
thank you and that worked for that portion but now i ran into another error that i could use some help with

checking for inet_ntoa... yes
checking for gethostbyname... yes
checking for gethostbyaddr... yes
checking for socket... yes
checking for connect... yes
checking for wresize in -lncurses... no
checking for wresize in -lcurses... no
configure: error: unable to find a curses library -- FATAL

---

### Post by poofyhairguy on 2004-12-06
try 

sudo apt-get install libncurses5

---

### Post by Darkenbay on 2004-12-06
tried that still got same error also i would like to say again that appericate all your help

---

### Post by Darkenbay on 2004-12-06
finally got it to install used "sudo apt-get install libncurses?" and it installed fully then reran the command and it completed the install

thank you all for your help

---

