---
title: "incompatible library ncurses (ubuntu 10.04.4 LTS lucid)"
date: 2012-11-18
forum: General Help
---

### Post by rnerwein on 2012-11-18
hello 
i have following problem when i try to compile my software using curseses i get:

downloading: wget [http://ftp.gnu.org/pub/gnu/ncurses/ncurses-5.7.tar.gz](http://ftp.gnu.org/pub/gnu/ncurses/ncurses-5.7.tar.gz)
i run following commands:
    ./configure     --> no errors
    make            --> no errors
    make install    --> no errors

but when i want to make my monitor i get:
    gcc -o yam -DYDEBUG -DKERNEL_6 -m64  yam.c ... yam_cpusingle -lnurses  -lnsl -lcrypt

    /usr/bin/ld:[COLOR=Blue] skipping incompatible[/COLOR] /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libncurses.so [COLOR=Blue]when searching for -lncurses[/COLOR]
    /usr/bin/ld: [COLOR=Blue]skipping incompatible [/COLOR]/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libncurses.a when searching for -lncurses
    /usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
    /usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses
    /usr/bin/ld:[COLOR=Blue] cannot find -lncurses[/COLOR]
    collect2: ld returned 1 exit status
   [COLOR=Red] make[1]: *** [yam] Fehler 1[/COLOR]

here my directory /usr/lib: ls -l libncurs*
    -rw-r--r-- 1 root richi  416130 2012-11-18 11:13 libncurses.a
    -rw-r--r-- 1 root richi  127100 2012-11-18 11:13 libncurses++.a
    -rw-r--r-- 1 root richi 2228358 2012-11-18 11:13 libncurses_g.a
    lrwxrwxrwx 1 root root       20 2012-11-17 17:43 libncurses.so -> /lib/libncurses.so.5
    lrwxrwxrwx 1 root richi      13 2012-11-17 17:46 libncurses.so.5 -> libtermcap.so
    -rw-r--r-- 1 root root   144208 2010-03-07 04:33 libncurses++w.a
    -rw-r--r-- 1 root root   424736 2010-03-07 04:33 libncursesw.a
    lrwxrwxrwx 1 root root       21 2012-11-17 17:50 libncursesw.so -> /lib/libncursesw.so.5

and my directory /lib: ls -l libncurs*
    lrwxrwxrwx 1 root root     17 2012-11-17 12:08 libncurses.so.5 -> libncurses.so.5.7
    -rw-r--r-- 1 root root 223768 2010-03-07 04:33 libncurses.so.5.7
    lrwxrwxrwx 1 root root     18 2012-11-17 12:10 libncursesw.so.5 -> libncursesw.so.5.7
    -rw-r--r-- 1 root root 272952 2010-03-07 04:33 libncursesw.so.5.7


my question is: what's wrong (yeah incompatible) and can anybody help me ?
i'm working on a sony vaio PCG-Z1RMP
    ubuntu lucid:
    Linux version 2.6.32-45-generic (buildd@aatxe) (gcc version 4.4.3
    (Ubuntu 4.4.3-4ubuntu5.1) ) #99-Ubuntu SMP Tue Oct 16 16:31:11 UTC 2012
    GNU ld (GNU Binutils for Ubuntu) 2.20.1-system.20100303

also installed binaries ( installed with apt-get install ... )
    libncurses5, libncurses5-dev, libcurses-dbg, libcursesw5, libcursesw5-dev
    libncursesw5-dbg

did anybody have an idea what can id do
thanks
   richi

---

### Post by zombifier25 on 2012-11-18
The "make install" should be "sudo make install" so that the ncurses libraries is installed into the system directories. There might be extra configuration, but none that I know of. Try recompiling and see if it works.

---

### Post by rnerwein on 2012-11-18
> **zombifier25 said:**
> The "make install" should be "sudo make install" so that the ncurses libraries is installed into the system directories. There might be extra configuration, but none that I know of. Try recompiling and see if it works.

hello 
excuse me - i don't tell - i was running as root.
thanks for reply
but i don't know whats going on.

---

### Post by raja.genupula on 2012-11-18
> /usr/bin/ld:[COLOR=Blue] skipping incompatible[/COLOR] /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libncurses.so [COLOR=Blue]when searching for -lncurses[/COLOR]
    /usr/bin/ld: [COLOR=Blue]skipping incompatible [/COLOR]/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../libncurses.a when searching for -lncurses
    /usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
    /usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses
    /usr/bin/ld:[COLOR=Blue] cannot find -lncurses[/COLOR]
    collect2: ld returned 1 exit status
   [COLOR=Red] make[1]: *** [yam] Fehler 1[/COLOR]

But this is saying that you got some error in making . so we need more information on both steps  like ./configure ,make and sudo make install . Then only we can give you proper solution to resolve your issue .

Thank you .

---

### Post by rnerwein on 2012-11-18
> **raja.genupula said:**
> But this is saying that you got some error in making . so we need more information on both steps  like ./configure ,make and sudo make install . Then only we can give you proper solution to resolve your issue .

Thank you .
ohhhhhh
thanks for the hint about makefile. yam is a kernelmonitor written by myself and is running on different system ( even solaris ).
i got a switch with "uname -r" in my makefile to figure out the options for gcc.
i installed my old sony with lucid (12.04 - no pae - don't boot). 
the error was between my ears. gcc was running with -m64 (uuuuuuuuuuuuuups)
thanks a lot
richi

---

