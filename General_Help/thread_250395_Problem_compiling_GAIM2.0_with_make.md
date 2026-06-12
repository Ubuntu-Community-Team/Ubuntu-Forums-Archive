---
title: "Problem compiling GAIM2.0 with make"
date: 2006-09-04
forum: General Help
---

### Post by Zarathu on 2006-09-04
```
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```

That's just the bottom half of the code after I run ./configure.

Any suggestions?  I don't know what to do here, and "make install" won't work post-configure.

---

### Post by croak77 on 2006-09-04
"checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool"

Install libxml-perl.

---

### Post by Zarathu on 2006-09-04
Awesome.  I did that, then I did "sudo make install" and everything went fine.  Now, where is(are) the file(s)?

---

### Post by Zarathu on 2006-09-04
Nevermind.  Got it working.

---

