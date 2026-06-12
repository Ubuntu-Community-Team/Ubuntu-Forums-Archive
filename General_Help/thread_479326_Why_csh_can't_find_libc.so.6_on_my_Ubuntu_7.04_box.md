---
title: "Why csh can't find libc.so.6 on my Ubuntu 7.04 box?"
date: 2007-06-20
forum: General Help
---

### Post by baosheng on 2007-06-20
hi, I am installing an electronic designing software called Cadence Allegro(part of SPB, Silicon Package Board).

I have finished the installation but when I wanna start it. It said:
forrest@flavia:/forrest/Applications/spb155/tools/pcb/bin$ allegro
/bin/csh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

But it was on the LD_LIBRARY_PATH.
forrest@flavia:/forrest/Applications/spb155/tools/pcb/bin$ csh -f
% env | grep LD_LIBRARY_PATH
LD_LIBRARY_PATH=/usr/lib/:/lib/:/forrest/Applications/ns-allinone-2.31/otcl-1.13:/forrest/Applications/ns-allinone-2.31/lib:/forrest/Applications/geda-install/lib:/lib/:/usr/lib:/forrest/Applications/spb155/tools/lib
% locate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6

I don't know why. Can anyone help me? 

I have run an script to set LD_ASSUME_KERNEL=2.4.1 otherwise "allegro" will report it can't find libdl.so.2
I am not sure whether this LD_ASSUME_KERNEL=2.4.1 makes CSH can't find libc.so.6

---

### Post by Beefeater on 2007-06-21
> **baosheng said:**
> hi, I am installing an electronic designing software called Cadence Allegro(part of SPB, Silicon Package Board).

I have finished the installation but when I wanna start it. It said:
forrest@flavia:/forrest/Applications/spb155/tools/pcb/bin$ allegro
/bin/csh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

But it was on the LD_LIBRARY_PATH.
forrest@flavia:/forrest/Applications/spb155/tools/pcb/bin$ csh -f
% env | grep LD_LIBRARY_PATH
LD_LIBRARY_PATH=/usr/lib/:/lib/:/forrest/Applications/ns-allinone-2.31/otcl-1.13:/forrest/Applications/ns-allinone-2.31/lib:/forrest/Applications/geda-install/lib:/lib/:/usr/lib:/forrest/Applications/spb155/tools/lib
% locate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6

I don't know why. Can anyone help me? 

I have run an script to set LD_ASSUME_KERNEL=2.4.1 otherwise "allegro" will report it can't find libdl.so.2
I am not sure whether this LD_ASSUME_KERNEL=2.4.1 makes CSH can't find libc.so.6

It is related to LD_ASSUME_KERNEL

Here is a fix
[http://gallery.menalto.com/node/50926](http://gallery.menalto.com/node/50926)

---

