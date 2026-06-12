---
title: "gaim/source compilation"
date: 2007-01-23
forum: General Help
---

### Post by usien on 2007-01-23
i want the latest version of gaim i.e ver 2 beta 6, but there are no .deb packages available from their website so i have to compile from the source.when i run ./configure i get this:

usien@usien-laptop:~/gaim-2.0.0beta6$ ./configure
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
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

the readme file says i need gtk 2 for this (including development files),could that be the problem or are these files already included in ubuntu.if not how do i get them?if i can get the binaries somewhere that would be better.

---

### Post by taurus on 2007-01-23
```
sudo aptitude update
sudo aptitude install build-essential
./configure
```

---

### Post by usien on 2007-01-25
thanx, i got over that, however this is what i get now(i tried downloading libglib2-dev and libglib2-dbg but doesnt help, do i need to update libc or is it something else?):

.
.
.
.
.
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... no
checking for GTK... no
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Gaim's
GTK+ interface.  If you only want to build the console interface then
specify --disable-gtkui when running configure.

---

### Post by lamego on 2007-01-25
You also need libgtk2.0-dev

---

### Post by usien on 2007-01-25
thanx, will get it.

---

### Post by ebash on 2007-01-25
You can ask apt-get to download the source dependencies for a package for you. In the case of gaim, chances are that the majority, if not all, of the dependencies can be resolved by the existing version of gaim in the repositories. In order to have apt-get download all the packages required for compiling the package do:

```
sudo apt-get build-dep gaim
```

---

