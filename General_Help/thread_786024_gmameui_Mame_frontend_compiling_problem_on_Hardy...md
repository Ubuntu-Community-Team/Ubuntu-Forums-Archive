---
title: "gmameui Mame frontend compiling problem on Hardy..."
date: 2008-05-07
forum: General Help
---

### Post by Moonfrost on 2008-05-07
I'm trying to install GMAMEUI which is a frontend for SDLMAME for Linux, I have to compile it so I tried the ./configure command first which works all the way up to one error at the end where it says "configure: error: cannot find zlib"...well, I installed zlib from the repos but it never detects no matter what I do...anybody who has experience compiling GMAME? I have the whole thing right here:

```
username@username-desktop:~/Desktop/gmameui-0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for strchr... yes
checking for inflate in -lz... no
configure: error: Cannot find zlib
```

---

### Post by NESFreak on 2008-10-18
have you installed zlib-dev ?

---

