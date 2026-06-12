---
title: "Xmms source compile fail?"
date: 2007-05-21
forum: General Help
---

### Post by thegrimgod on 2007-05-21
Hi al,i tried to compile xmms from the source file, as far as i saw ./configure ran well, when i did make i got this:
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT -I../../intl -I../.. -g -O2 -Wall -Wpointer-arith -finline-functions -ffast-math -funroll-all-loops -MT ir.lo -MD -MP -MF .deps/ir.Tpo -c ir.c  -fPIC -DPIC -o ir.lo
ir.c:19: error: static declaration of 'keepGoing' follows non-static declaration
ir.h:53: error: previous declaration of 'keepGoing' was here
ir.c:22: error: static declaration of 'irapp_thread' follows non-static declaration
ir.h:52: error: previous declaration of 'irapp_thread' was here
make[3]: *** [ir.lo] Error 1
make[3]: Leaving directory `/home/grim/xmms-1.2.10/General/ir'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/grim/xmms-1.2.10/General'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/grim/xmms-1.2.10'
make: *** [all] Error 2
and then since i thought i would go to the end with it i did a make install and got this :
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -D_REENTRANT -I../../intl -I../.. -g -O2 -Wall -Wpointer-arith -finline-functions -ffast-math -funroll-all-loops -MT ir.lo -MD -MP -MF .deps/ir.Tpo -c ir.c  -fPIC -DPIC -o ir.lo
ir.c:19: error: static declaration of 'keepGoing' follows non-static declaration
ir.h:53: error: previous declaration of 'keepGoing' was here
ir.c:22: error: static declaration of 'irapp_thread' follows non-static declaration
ir.h:52: error: previous declaration of 'irapp_thread' was here
make[2]: *** [ir.lo] Error 1
make[2]: Leaving directory `/home/grim/xmms-1.2.10/General/ir'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/grim/xmms-1.2.10/General'
make: *** [install-recursive] Error 1
Now the odd part is that xmms works , so what happened?

---

### Post by bung33 on 2007-05-22
It could be that some of the plugins failed compilation, but that the main program itself didn't encounter any serious errors. However, I would install the latest version using the synaptic package manager. Just search for xmms and it will automatically install and resolve any dependencies...

---

### Post by yohan funkyfresh bach on 2008-06-05
you should just use vlc. xmms is outdated now. vlc media player plays everything from movies to music thats what you want

---

