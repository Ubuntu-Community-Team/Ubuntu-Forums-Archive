---
title: "mutt problems: unable to use .muttrc"
date: 2018-11-30
forum: General Help
---

### Post by scholz-thispla on 2018-11-30
I've just installed the current Kubuntu on a new laptop and experience a problem with mutt. It's the third time I switch machines, change to a new Kubuntu, and copy my data. The last two times, all worked out of the box. Although I see the problem with mutt, I have the feeling that it is a more general problem. 


[LIST]
[*]I installed mutt via Discover and copied the .muttrc file from my old machine. 
[*]When I just run "mutt", it seems as if my .muttrc is not read 
[*]running "mutt -F .muttrc" gives ".muttrc: Permission denied" 
[*]"mutt -F /home/scholz/.muttrc" gives "/home/scholz/.muttrc: Permission denied" 
[*]then I copy .muttrc as root to /tmp and execute "/snap/bin/mutt -F /tmp/.muttrc" as root. This gives "/tmp/.muttrc: No such file or directory" 
[/LIST]

Needless to say, all these files exist and are readable (-rw-r--r--). I also repeated all steps with empty .muttrc files, to make sure the messages are about reading the file itself, not about problems with the content.

What I can do is start mutt (apparently without .muttrc) and change to one of my copied mailboxes.  They are read fine

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.10
DISTRIB_CODENAME=cosmic
DISTRIB_DESCRIPTION="Ubuntu 18.10"

 mutt -v
Mutt 1.11 (3b75515) (2018-11-25)
Copyright (C) 1996-2016 Michael R. Elkins and others.
Mutt comes with ABSOLUTELY NO WARRANTY; for details type `mutt -vv'.
Mutt is free software, and you are welcome to redistribute it
under certain conditions; type `mutt -vv' for details.

System: Linux 4.18.0-11-generic (x86_64)
ncurses: ncurses 6.0.20160213 (compiled with 6.0)
libidn: 1.32 (compiled with 1.32)
hcache backend: tokyocabinet 1.4.48

Compiler:
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/5/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 5.4.0-6ubuntu1~16.04.10' --with-bugurl=file:///usr/share/doc/gcc-5/README.Bugs --enable-languages=c,ada,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-5 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-5-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-5-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-5-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.10) 

Configure options: '--prefix=' '--enable-compressed' '--enable-debug' '--enable-fcntl' '--enable-hcache' '--enable-gpgme' '--enable-lua' '--enable-imap' '--enable-smtp' '--enable-pop' '--enable-sidebar' '--enable-nntp' '--disable-dotlock' '--disable-fmemopen' '--with-curses' '--with-gnutls' '--with-gss' '--with-idn' '--with-mixmaster' '--with-sasl' '--without-gdbm' '--without-bdb' '--without-qdbm' 'LDFLAGS= -L/build/mutt/parts/mutt/install/lib -L/build/mutt/parts/mutt/install/usr/lib -L/build/mutt/parts/mutt/install/lib/x86_64-linux-gnu -L/build/mutt/parts/mutt/install/usr/lib/x86_64-linux-gnu'

---

### Post by howefield on 2018-11-30
How did you install Mutt ?

Permissions on my .muttrc (18.10 packaged version 1.10.1) are -rw-rw-r--

---

### Post by scholz-thispla on 2018-11-30
Thanks, your answer triggered some actions that helped. I had installed mutt via Discover. Now I uninstalled it (again via Discover) and reinstalled it via "sudo apt-get install mutt urlview". In addition, I had to remove the now obsolete hash (/snap/bin/mutt) by "hash mutt". Then, mutt suddenly started to work.

---

### Post by howefield on 2018-11-30
Cool, glad you figured it out.

---

