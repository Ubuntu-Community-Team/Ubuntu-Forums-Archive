---
title: "Peer Guardian 2.2.3 install issues  ( tar.gz missing packages )"
date: 2014-01-20
forum: General Help
---

### Post by steve6 on 2014-01-20
Running Ubuntu 13.10 64bit 

Trying to install Peer Guardian 2.2.3 (the latest Peer Guardian via SourceForge.net) 

pgl-2.2.3.tar.gz

I'm trying to install the traditional way 

```
sudo ./configure && make && make install
```

But I run into this message

```
checking for libnetfilterqueue... no
configure: error: Package requirements (libnetfilter_queue) were not met:

No package 'libnetfilter_queue' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libnetfilterqueue_CFLAGS
and libnetfilterqueue_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
user@user:~/Desktop/pgl-2.2.3$ 

```


How do I install all the packages at once and is there anything I may have to deal with down the way?
Thanks,
SW


Here is the whole message in case it is needed.
```
user@user:~$ cd Desktop
user@user:~/Desktop$ cd pgl-2.2.3
user@user:~/Desktop/pgl-2.2.3$ ./configure && make && sudo make install
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking for ar... ar
checking the archiver (ar) interface... ar
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/user/missing: No such file or directory
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking whether make supports nested variables... yes
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking for inttypes.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for inline... inline
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint8_t... yes
checking for error_at_line... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for memchr... yes
checking for memmove... yes
checking for memset... yes
checking for strdup... yes
checking for strerror... yes
checking for strstr... yes
checking for libnetfilterqueue... no
configure: error: Package requirements (libnetfilter_queue) were not met:

No package 'libnetfilter_queue' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libnetfilterqueue_CFLAGS
and libnetfilterqueue_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
user@user:~/Desktop/pgl-2.2.3$ 

```

---

### Post by jre on 2014-01-21
You'd need some special configure options, see the INSTALL file in the tar.gz

But why do that on ubuntu? I offer a repository with pgl packages at [https://launchpad.net/~jre-phoenix/+archive/ppa](https://launchpad.net/~jre-phoenix/+archive/ppa). See [https://sourceforge.net/p/peerguardian/wiki/pgl-Main/](https://sourceforge.net/p/peerguardian/wiki/pgl-Main/)


btw, Hello again to all. I hadn't been here since the server hack.

---

### Post by steve6 on 2014-01-21
jre-
Thank you for getting back to me on this and who better than one of the developers. Awesome!
 
I tried the steps on [http://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/](http://sourceforge.net/p/peerguardian/wiki/pgl-Install-DebianUbuntu/) and the program "pglgui" did work, sortof. 
2 similar error windows keep popping up, each error window displays that "Command: which gksu | Output: (None)" 
How do I fix this?

This is also why I wanted to compile/build it myself. I figured by doing it this way I could 
1) in the process obtain whatever it was I was lacking
2) gain expirence because I still do not understand what Linux repositories, packages or dependancies are, or the difference between them.

Any help or good links to other forums would be greatly appriciated.

---

### Post by jre on 2014-01-22
To compile you need to install the development headers of pgl's build dependencies.

btw the runtime dependencies are (should be if I didn't miss anything) installed automatically if you installed from the repository.

Except the documentation in pgl and the wiki I've unfortunately no links available.

Do you have "which" installed? Try
```
 which which
```
Do you have gksu(do) or kdesu(do) installed? If you have which installed then now try
```
which gksu gksudo kdesu kdesudo
```

---

