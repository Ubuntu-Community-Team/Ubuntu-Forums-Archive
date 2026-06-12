---
title: "Install Fuse for use with gmailFS...having trouble with kernel source."
date: 2005-04-01
forum: General Help
---

### Post by dougr on 2005-04-01
I am trying to install fuse for use with gmailFS.

When i try to mount a drive using gmailFS, I get the following error.

> doug@xxxx:~/My Downloads/fuse-2.2.1 $ sudo /usr/share/gmailfs/gmailfs.py /media/gmailfs noauto,username=xxxxxxxx,password=xxxxxxx,fsname=xxxxxxx
INFO:gmailfs:Connected to gmail
FATAL: Module fuse not found.
fusermount: fuse device not found, try 'modprobe fuse' first
fuse: reading device: Bad file descriptor 

Obviously the things I downloaded using synaptec have not worked, so I try to compile fuse from source.

I get the following error:

> doug@xxxxxxx:~/My Downloads/fuse-2.2.1 $ sudo ./configure --with-kernel=usr/src/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/doug/My: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from  object... ok
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for setxattr... yes
checking for struct stat.st_atim... yes
configure: creating ./config.status
config.status: creating fuse.pc
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating util/Makefile
config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
configure: configuring in kernel
configure: running /bin/sh './configure' --prefix=/usr/local  '--with-kernel=usr/src/' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... usr/src/
checking kernel source version... Not found
configure: error:
*** Cannot determine the version of the linux kernel source. Please
*** configure the kernel before running this script
configure: error: /bin/sh './configure' failed for kernel 


I realize what I am specifying as kernel source is wrong, but I do not know what to use.  So I run uname-a, and this is what I get.

> doug@xxxxx:~/My Downloads/fuse-2.2.1 $ uname -a Linux xxxxx 2.6.10-5-386 #1 Wed Mar 30 19:46:52 BST 2005 i686 GNU/Linux 

problem is that I cannot find kernel headers for 2.6.10-5-386 in the synaptec repository.  I have no idea what to do at this point.  Please help!

---

### Post by Locomorto on 2005-04-01
I think the package is called linux-header(s)-<kernal version>

---

### Post by dougr on 2005-04-01
Thanks that fixed it...

Now I am having problems running make.

> doug@xxxxx:~/My Downloads/fuse-2.2.1 $ make
Making all in kernel
make[1]: Entering directory `/home/doug/My Downloads/fuse-2.2.1/kernel'
make -C /usr/src/linux-headers-2.6.10-5-386 SUBDIRS=/home/doug/My Downloads/fuse-2.2.1/kernel  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
make[2]: *** No rule to make target `Downloads/fuse-2.2.1/kernel'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [all-spec] Error 2
make[1]: Leaving directory `/home/doug/My Downloads/fuse-2.2.1/kernel'
make: *** [all-recursive] Error 1 

any ideas?

Thanks

---

### Post by clov on 2005-09-27
same problem here? can anybody help?

>  /home/clov/Desktop/fuse-2.3.0# make
Making all in kernel
make[1]: Entering directory `/home/clov/Desktop/fuse-2.3.0/kernel'
make -C /usr/src/linux-headers-2.6.12-9 SUBDIRS=/home/clov/Desktop/fuse-2.3.0/kernel  modules
/bin/sh: /usr/src/linux-headers-2.6.12-9/scripts/gcc-version.sh: No such file or directory
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[3]: scripts/Makefile.build: No such file or directory
make[3]: *** No rule to make target `scripts/Makefile.build'.  Stop.
make[2]: *** [_module_/home/clov/Desktop/fuse-2.3.0/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9'
make[1]: *** [all-spec] Error 2
make[1]: Leaving directory `/home/clov/Desktop/fuse-2.3.0/kernel'
make: *** [all-recursive] Error 1



Problem solved!!! I had a != gcc version.
New problem found! 
> 
:/home/clov/Desktop/fuse-2.3.0/example# ./hello /tmp/fuse -d
FATAL: Error inserting fuse (/lib/modules/2.6.12-9-686/kernel/fs/fuse/fuse.ko): Invalid module format
fusermount: fuse device not found, try 'modprobe fuse' first


...and then...
> 
/home/clov/Desktop/fuse-2.3.0/example# modprobe fuse
FATAL: Error inserting fuse (/lib/modules/2.6.12-9-686/kernel/fs/fuse/fuse.ko): Invalid module format


any clues?

---

