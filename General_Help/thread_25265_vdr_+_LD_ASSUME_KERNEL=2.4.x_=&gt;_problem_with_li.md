---
title: "vdr + LD_ASSUME_KERNEL=2.4.x =&gt; problem with libpthread"
date: 2005-04-09
forum: General Help
---

### Post by tkw on 2005-04-09
Hello.

I'm running Hoary and trying to set up VDR (1.3.23) to use my PC as a digibox+digital video recorder, connected to my TV. (Please, don't suggest apt-getting the vdr package from the repositories, because I cannot use the vdr 1.2.x package from Ubuntu .deb repositories, because I have a "budget" card, and those are is not supported by that package even though they are supported by vdr.)

I've faced a problem I cannot solve myself. Please help. Below, you find more details:

VDR does not support NPTL (Native Posix Thread Library). The workaround is to use 'export LD_ASSUME_KERNEL=2.4.1' before running VDR. This just doesn't work for me.

When running VDR, I get the following error:

[FONT=Courier New]tom@posetiivi:~ $ vdr -Pxine
vdr: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
[/FONT]

libpthread exists:
tom@posetiivi:~/vdr $ locate libpthread
/usr/lib/libpthread.a
/usr/lib/libpthread_nonshared.a
/usr/lib/libpthread.so
/lib/libpthread.so.0
/lib/libpthread-0.60.so
/lib32/tls/libpthread-0.60.so
/lib32/tls/libpthread.so.0
/lib32/libpthread-0.10.so
/lib32/libpthread.so.0 

Also /etc/ld.so.conf contains all the needed paths and ldconfig has been run.

Executing 'ldconfig -p' shows among other things the following interesting thing about libpthread:

libpthread.so.0 (libc6, hwcap: 0x8000000000000000, OS ABI: Linux 2.6.0)
=> /lib32/tls/libpthread.so.0
        libpthread.so.0 (libc6, OS ABI: Linux 2.2.0) => /lib32/libpthread.so.0

There is no row saying "OS ABI: Linux 2.4.0"  for libpthread. My friend is running Fedora Core X with VDR and LD_ASSUME_KERNEL=2.4.20 working fine. His ldconfig shows a row for libpthread showing "ABI: Linux 2.4.20".

I assume this makes the difference. Who could provide such a libpthread for Ubuntu, that would have the correct ABI? Or is there some other way to make LD_ASSUME_KERNEL=2.4.1 work with Hoary?


My system is:

Hoary (pre-release version, impossible to give exact information, since I have updated packages manually from Synaptic after upgrade from Warty to Hoary pre-release version in Feb-March).

gcc:
tom@posetiivi:~/vdr $ gcc -v
Reading specs from /usr/lib/gcc-lib/x86_64-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc --disable-multilib x86_64-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)


Kernel:
Linux posetiivi 2.6.10-5-amd64-k8 #1 Tue Mar 15 14:42:38 UTC 2005 x86_64 GNU/Linux

libc6 ja libc6-dev:
2.3.2.ds1-20ubuntu8

libgcc1: 1:4.0-0pre6ubuntu7

lib32gcc1: 4.0-0pre6ubuntu5

g++:
Koodi:

tom@posetiivi:~/vdr $ g++ -v
Reading specs from /usr/lib/gcc-lib/x86_64-linux/3.3.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,java,f77,pascal,objc,ada,treelang --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-gxx-include-dir=/usr/include/c++/3.3 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --enable-__cxa_atexit --enable-clocale=gnu --enable-debug --enable-java-gc=boehm --enable-java-awt=xlib --enable-objc-gc --disable-multilib x86_64-linux
Thread model: posix
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)

I've successfully compiled xine-lib, xine-ui and vdr 1.3.23 on my PC, and I'm using the DVB drivers from the 2.6.10 kernel, but this threading problem is just too difficult for me to solve, as a relatively newbie Linux user.

All help is welcome! Thanks in advance. :-)

Tom

---

### Post by mtron on 2005-04-11
Did you suceed with setting it up? 

I have also a Budget Card (WINTV Nova) found that WIKI: [http://www.linuxtv.org/vdrwiki/index.php/Main_Page](http://www.linuxtv.org/vdrwiki/index.php/Main_Page)

I'll come back and tell you what I was able to do.

---

### Post by tkw on 2005-04-13
No, I have not succeeded yet.

Yesterday I trid dist-upgrade in the hope that the released version of Hoary packages would have "OS ABI: Linux 2.4.x" for libpthread. It seems the ABIs have remained the same: Linux 2.2 and Linux 2.6 are mentioned in 'ldconfig -p' output.

In addition to this problem persisting, the upgrade also broke my X.org, but that's another story and not part of this thread. I'll try to find help in the forums. :-(

BR, TKW

---

### Post by tkw on 2005-04-16
I continue my lonely diary of hunting this bug / solving the problem:

I found out that libpthread is a part of libc6. (Yes, that was probably clear for most of you, but not for me  - a Linux newbie. :)

I also found out that LD_ASSUME_KERNEL > 2.6.0 has created problems with libc on Debian also before:

[http://lists.debian.org/debian-glibc/2004/01/msg00118.html](http://lists.debian.org/debian-glibc/2004/01/msg00118.html)

"
#226716: libc6: TLS doesn't work with LD_ASSUME_KERNEL < 2.6.0
Package: libc6; Severity: important; Reported by: Juergen Kreileder 
1 year and 99 days old.
"

C'mon. Does anyone have a working Ubuntu/Debian based VDR box with libc6 version > 2.3.2.ds1-10, AMD64 2.6.x kernel and VDR 1.3.x? It starts looking as if my combination will never work. :-(

TKW

---

### Post by mtron on 2005-12-21
well for my part i switched to debian sarge cause i found a apt source with nice good working vdr packages for budget cards, even with sc...

---

