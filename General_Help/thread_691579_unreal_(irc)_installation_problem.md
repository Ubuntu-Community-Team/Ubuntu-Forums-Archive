---
title: "unreal (irc) installation problem"
date: 2008-02-08
forum: General Help
---

### Post by ahmbay on 2008-02-08
```
./Config

./configure --with-showlistmodes --enable-hub --with-listen=5 --with-dpath=/root/irc2/u/Unreal3.2 --with-spath=/root/irc2/u/Unreal3.2/src/ircd --with-nick-history=2000 --with-sendq=3000000 --with-bufferpool=18 --with-hostname=ubuntu --with-permissions=0600 --with-fd-setsize=1024 --enable-dynamic-linking
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables

 _______________________________________________________________________
|                                                                       |
|                    UnrealIRCd Compile-Time Config                     |
|_______________________________________________________________________|
|_______________________________________________________________________|
|                                                                       |
| Now all you have to do is type 'make' and let it compile. When that's |
| done, you will receive other instructions on what to do next.         |
|                                                                       |
|_______________________________________________________________________|
|_______________________________________________________________________|
|                        - The UnrealIRCd Team -                        |
|                                                                       |
| * Stskeeps  stskeeps@unrealircd.com                                   |
| * codemastr codemastr@unrealircd.com                                  |
| * Syzop     syzop@unrealircd.com                                      |
|_______________________________________________________________________|
root@ubuntu:~/irc2/u/Unreal3.2# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:~/irc2/u/Unreal3.2#
```



i cant do that,
when i try to setup gcc compiler i get this error


```
root@ubuntu:~/irc2/u/tcl8.4.12/unix# ./configure
creating cache ./config.cache
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
root@ubuntu:~/irc2/u/tcl8.4.12/unix# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:~/irc2/u/tcl8.4.12/unix#
```

---

### Post by taurus on 2008-02-08
You need to install the build-essential package first before you run ./configure.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by tosk on 2008-02-08
```
sudo apt-get install build-essential
```

Do you have **build-essential** installed?

//edit-doh! I fail! :P I've been beaten!

---

### Post by ahmbay on 2008-02-11
ok,
i ve installed the build-essential package

but now when i try to install tcl i get this error
```
root@ubuntu:~/irc/x/tcl8.4.12/unix# ./configure
creating cache ./config.cache
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking dirent.h...
checking for errno.h... yes
checking for float.h... yes
checking for values.h... yes
checking for limits.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for sys/wait.h... yes
checking for dlfcn.h... yes
checking for unistd.h... yes
checking for sys/param.h... yes
checking if the compiler understands -pipe... yes
checking for building with threads... no (default)
checking for sin... no
checking for main in -lieee... yes
checking for main in -linet... no
checking for net/errno.h... no
checking for connect... yes
checking for gethostbyname... yes
checking how to build libraries... shared
checking for ranlib... ranlib
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)... ./configure: 1: Syntax error: Unterminated quoted string
root@ubuntu:~/irc/x/tcl8.4.12/unix# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:~/irc/x/tcl8.4.12/unix# make install
make: *** No rule to make target `install'.  Stop.
root@ubuntu:~/irc/x/tcl8.4.12/unix#
```

---

