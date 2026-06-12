---
title: "QEMU Compile Problem"
date: 2007-02-08
forum: General Help
---

### Post by opus on 2007-02-08
I am trying to get the latest version of qemu (0.9.0) working with the latest release of kqemu (1.3.0pre11, the newly open-sourced one).  I haven't even made it as far as setting up kqemu because I can't even get qemu to compile.  It looks like it configures okay, but after there is no makefile, and the 'make' command doesn't work - it says no targets and no makefile.

I am running Ubuntu Edgy.  Here is the output from my terminal:

```
user@computer:~/qemu-0.9.0$ ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/lib/modules/$(uname -r)/build/
Install prefix    /usr
BIOS directory    /usr/share/qemu
binary directory  /usr/bin
Manual directory  /usr/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/aaron/qemu-0.9.0
C compiler        gcc-3.4
Host C compiler   gcc-3.4
make              make
install           install
host CPU          i386
host big endian   no
target list       i386-linux-user arm-linux-user armeb-linux-user sparc-linux-user ppc-linux-user mips-linux-user mipsel-linux-user m68k-linux-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu mipsel-softmmu arm-softmmu
gprof enabled     no
profiler          no
static build      no
SDL support       yes
SDL static link   yes
mingw32 support   no
Adlib support     no
CoreAudio support no
ALSA support      no
DSound support    no
FMOD support      no 
kqemu support     yes
Documentation     yes
user@computer:~/qemu-0.9.0$ make
make: *** No targets specified and no makefile found.  Stop.
```

Any ideas?

---

### Post by Rommidze on 2007-03-01
There is packaged variant of original [qemu 9 build in my repository]("http://tech.tolero.org/blog/en/linux/qemu-9-and-kqemu-for-ubuntu-dapper-edgy-feisty"). kqemu packages and instructions are also provided.

---

