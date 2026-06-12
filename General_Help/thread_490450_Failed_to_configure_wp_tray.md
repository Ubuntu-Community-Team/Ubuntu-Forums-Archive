---
title: "Failed to configure wp_tray"
date: 2007-07-02
forum: General Help
---

### Post by DrObviousSo on 2007-07-02
I've downloaded the latest source code for [wp_tray]("http://planetearthworm.com/projects/wp_tray/index.php"), and have tried to compile it on my Feisty AMD64 machine.  The ./compile command fails, and gives me this output:

> drobvious@uKermit:~/Desktop/wp_tray-0.5.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (libgnomeuimm-2.6 >= 2.6.0                         gconfmm-2.6 >= 2.6.0                         gtkmm-2.4 >= 2.4.0                         libgnomecanvasmm-2.6 >= 2.6.0                         libglademm-2.4 >= 2.4.0                         libpanelapplet-2.0 >= 2.0.0                         libxml++-2.6                         libnotify >= 0.3.0) were not met:

No package 'libgnomeuimm-2.6' found
No package 'gconfmm-2.6' found
No package 'gtkmm-2.4' found
No package 'libgnomecanvasmm-2.6' found
No package 'libglademm-2.4' found
No package 'libpanelapplet-2.0' found
No package 'libxml++-2.6' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
I tried searching for the packages listed after "No package '***' found in the gui package manager, but couldn't find any of them.  I assume I need to install the, but I don't know how to go about doing that.

---

### Post by Brucevdk on 2007-07-02
> **DrObviousSo said:**
> I tried searching for the packages listed after "No package '***' found in the gui package manager, but couldn't find any of them.  I assume I need to install the, but I don't know how to go about doing that.

Those names never point to the actual packages for example if it complains about *gtkmm-2.4* you'll have to install *libgtkmm-2.4-dev*. Same with the other ones.

However, there's a much easier way to get all the dependencies for the *wallpaper-tray* package and that is by executing the following command:
```

sudo apt-get build-dep wallpaper-tray

```

Where build-dep obviously stands for build-dependencies, this'll fetch all the packages needed to compile the application from source.

---

### Post by DrObviousSo on 2007-07-03
Thanks for your help.  I managed to get all the dependencies installed, though I had to do it manually [as described here.]("http://ubuntuforums.org/archive/index.php/t-144750.html")

So I went to configure again, and I got this error message:
> configure: error: You must call configure with the --with-boostregex option.
    This tells configure where to find the Boost Regex C++ library.
    e.g. --with-boostfilesystem=/usr/local/boostregex.so


I googled "boostregex.so", but only got 2 results that didn't really help at all.  Any suggestions?

Thanks.

---

### Post by Brucevdk on 2007-07-03
How about:
```

sudo apt-get install libboost-regex-dev

```

That package includes */usr/lib/libboost_regex.so*, you can probably even skip the *--with* switch.

---

### Post by DrObviousSo on 2007-07-03
Hmmm... gut check.  I installed that package, and am now calling
> ./configure --with-boostfilesystem=/usr/lib/libboost_regex.so
and it is still giving me the same 
> configure: error: You must call configure with the --with-boostregex option.
    This tells configure where to find the Boost Regex C++ library.
    e.g. --with-boostfilesystem=/usr/local/boostregex.so


Am I making a syntactical mistake?  (and yeah, I tried just ./configure, but that gave the same error)

Thanks a lot for your help.  I really appreciate it.

---

### Post by Brucevdk on 2007-07-03
> **DrObviousSo said:**
> Am I making a syntactical mistake?  (and yeah, I tried just ./configure, but that gave the same error)

Yes you are actually (and I was incorrect about making the assumption you wouldn't need *--with*).
```

./configure --with-boostfilesystem=/usr/lib/libboost_regex.so

```
You're use* --with-boostfilesystem* for the Boost Regex Library. What you need to execute is (that is if you have all the necessary libraries:
```

./configure --with-boostfilesystem=/usr/lib/libboost_filesystem.so --with-boostregex=/usr/lib/libboost_regex.so

```

Oh and it seems the Debian package for wallpaper-tray doesn't define any build-dependencies so build-dep doesn't' work anyways.

---

