---
title: "How to install libpng 1.5.15 on 19.10"
date: 2020-01-29
forum: General Help
---

### Post by greg9964 on 2020-01-29
Hi, I need libpng 1.5.15 to run Maya 2020 from Autodesk. This version of libpng is so old that I have to compile it.
When I run the ./configure command, the terminal gives the error that zlib isn't installed.

```
[FONT=monospace][COLOR=#000000]hecking for a BSD-compatible install... /usr/bin/install -c[/COLOR]
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /usr/bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...  
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /usr/bin/sed
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for fgrep... /usr/bin/grep -F
checking how to print strings... printf
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for a sed that does not truncate output... (cached) /usr/bin/sed
checking for gawk... (cached) mawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu 
format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_
convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries...
 yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for C/C++ restrict keyword... __restrict
checking for working strtod... yes
checking for memset... yes
checking for pow... no
checking for pow in -lm... yes
checking for zlibVersion in -lz... no
checking for z_zlibVersion in -lz... no
configure: error: zlib not installed

[/FONT]
```

It seems that zlib is installed by default in Ubuntu, so I tried compiling a version of it from around the time that libpng 1.5.15 was released, and well I'm gonna have to reinstall the OS tomorrow (:

So my question would be is there a work around that would allow me to install this old version of libpng along side the new version of zlib or is there a way to install the old version of zlib without corrupting my system?

---

