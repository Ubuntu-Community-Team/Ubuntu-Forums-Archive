---
title: "Recompile kernel"
date: 2007-02-18
forum: General Help
---

### Post by amwus on 2007-02-18
Hello all... I'm new here and I'm from Belgium, so I don't speak English very well... sorry :) 

So, here is my problem... I'd like to recompile my kernel on my Ubuntu edgy eft, in order to activate pentium M full support. So i downloaded all the necessary packages and i decompressed the archive in /usr/src. After that, i created a link to the source folder :
sudo ln -s linux-source-2.6.20 linux. 

It worked well.  But, when i try to use make menuconfig command, i've many errors !!! It's the first time I've this problem and I don't know why :

> 
root@nefron:/usr/src/linux# make menuconfig
  HOSTCC  scripts/basic/fixdep
In file included from /usr/include/bits/posix1_lim.h:153,
                 from /usr/include/limits.h:145,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/include/bits/local_lim.h:36:26: error: linux/limits.h: Aucun fichier ou répertoire de ce type
In file included from /usr/include/sys/socket.h:35,
                 from /usr/include/netinet/in.h:24,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:115:
/usr/include/bits/socket.h:304:24: error: asm/socket.h: Aucun fichier ou répertoire de ce type
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:204: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:204: error: for each function it appears in.)
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
make[1]: *** [scripts/basic/fixdep] Erreur 1
make: *** [scripts_basic] Erreur 2


How can i resolve this problem ? 

Thank you very much ! 

Greetings 8)

---

### Post by capdog on 2007-02-20
There's a thread called "Master Kernel" thread, search for it... all the details are there.

Follow them, hopefully it'll work! Try make xconfig instead of menuconfig.

---

