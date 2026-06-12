---
title: "ld-linux.so.2 Missing? Eh?"
date: 2006-11-17
forum: General Help
---

### Post by xianthax on 2006-11-17
i'm in the process of installing VMWare on a Ubuntu drapper x64 server system.  during the running of the config program "vmware-config.pl" I get this error:

/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)

/lib/ld-linux.so.2 appears to be MIA, this is my first time playing with a 64-bit linux install, has this file been moved / renamed vs 32bit systems? if so what to so i can create a link? 
its my understanding that this library probably should have been there as part of the base install or atleast been put in place when i installed gcc + other build tools, is that right?  

strangly enough the vmware install and config script say they completed successfully but some of the vmware bin files are missing vmware-vmx for instance, i would think the install script would have died if that binary didn't get created but meh.

thanks in advance.

-xian

---

### Post by xianthax on 2006-11-17
problem solved...

for future reference to build/install VMware server you need to install the "ia32-libs" package if you are using a 64bit OS.

-xian

---

