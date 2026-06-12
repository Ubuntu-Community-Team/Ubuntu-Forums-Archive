---
title: "problems with glib during ./configure"
date: 2008-04-26
forum: General Help
---

### Post by seansoni on 2008-04-26
I am trying to install AIMject 1.0.  During ./configure I get this:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ANSI C header files... (cached) yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for unistd.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for sys/types.h... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
found
checking for GTHREAD... yes
found
checking for GMODULE... yes
found
checking for GTK... no
configure: error: failed to find gtk-2.0 >= 2.6

What should I do know...When I downloaded gtk off the internet and tried to install it, I needed to download more things for that... it seems like an endless cycle.  Is there an easier way to install these things?  Thanks!  (I'm new to Linux).

---

### Post by arkangel on 2008-04-30
[PHP]sudo aptitude install libgtk2.0-dev[/PHP]

---

