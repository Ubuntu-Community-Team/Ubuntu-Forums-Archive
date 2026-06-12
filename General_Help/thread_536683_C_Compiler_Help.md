---
title: "C Compiler Help"
date: 2007-08-28
forum: General Help
---

### Post by kinngg on 2007-08-28
chilin@chilin-laptop:~/Downloads$ cd pidgin-2.1.1
chilin@chilin-laptop:~/Downloads/pidgin-2.1.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Why can't my C compiler create executables? thank you

---

### Post by jediborger on 2007-08-28
Do you have the package build-essentials installed? if so then try reinstalling gcc.

---

### Post by zoobave on 2007-08-28
Check the permissions
Post your config.log file

---

### Post by Dark Star on 2007-08-28
It  seems you did not have a C/C++ compiler do this

To install G++ 1'st open Terminall.. and type this
```
sudo apt-get install g++
```

Then after this gets done

```
sudo apt-get install build-essential
```

Hope this helps :D

---

### Post by kinngg on 2007-08-28
You must have the GLib 2.0 development headers installed to build 

i installed build essential and all that now i have a new problem what is this?

---

### Post by kranny on 2007-08-29
me gotta same prblm....no package build essential found

---

