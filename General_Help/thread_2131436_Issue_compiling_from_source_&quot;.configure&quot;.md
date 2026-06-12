---
title: "Issue compiling from source &quot;./configure&quot; works &quot;make&quot; fails &quot;Error 1&quot;"
date: 2013-04-01
forum: General Help
---

### Post by Dude Random21 on 2013-04-01
Hey guys, I've posted previously hopping for support with my new printer (xerox workcenter 6015NI) but in vain. Was hopping someone knew a way to fix the driver but it appears not. So I'm going back the the ghostscript method I found just need help with that.

For the foohbpl driver I need ghostscript 8.54 which must be compiled from source, as the tile suggests ./configure worked fine but once I get to the make command I get this error:
```
./src/pipe_.h:39:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]In file included from ./src/gp_unix.c:19:0:
./src/time_.h:47:8: error: redefinition of ‘struct timeval’
/usr/include/i386-linux-gnu/bits/time.h:31:8: note: originally defined here
./src/gp_unix.c: In function ‘gp_get_realtime’:
./src/gp_unix.c:99:2: warning: implicit declaration of function ‘gettimeofday’ [-Wimplicit-function-declaration]
make: *** [obj/gp_unix.o] Error 1
```

This occurs very quickly after I run "make" (53 lines in terminal). I can provide any further information upon request.

Many thanks to anyone offering help!

---

### Post by d0006 on 2013-04-01
Maybe some ideas here: [http://forum.xplico.org/viewtopic.php?p=2](http://forum.xplico.org/viewtopic.php?p=2)
I have found it worthwhile to do a search on the error messages.

---

