---
title: "Error compiling Gimp plug-in: Freetype"
date: 2007-08-07
forum: General Help
---

### Post by skrehnbrink on 2007-08-07
I'm running into an error when trying to compile the Freetype plug-in for GIMP.  I'm completely stumped and would appreciate any help I can get.  Here is the error I am receiving:

skrehnbrink@343-krehnbrink-linux:~/gimp-freetype-0.6$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for unistd.h... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking for gimp-2.0 gimpui-2.0... Package gimp-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimp-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimp-2.0' found Package gimpui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gimpui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gimpui-2.0' found
configure: error: Library requirements (gimp-2.0 gimpui-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
et


The .pc libraries do not exist on my system, I have GIMP installed.

---

### Post by apetresc on 2007-08-07
This should help you: ```
sudo apt-get install libgimp2.0-dev
```

---

### Post by skrehnbrink on 2007-08-09
Yahtzee!  Thanks!

---

