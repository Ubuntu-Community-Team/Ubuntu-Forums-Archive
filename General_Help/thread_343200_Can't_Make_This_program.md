---
title: "Can't Make This program"
date: 2007-01-21
forum: General Help
---

### Post by fokuslee on 2007-01-21
[http://vleu.net/shake/](http://vleu.net/shake/)
can any please let me know if they are able to make it? 
i just installed build-essential 
since the source contains Makefile 
so i just used sudo make 
I get this

cc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.28\" -DNDEBUG -c executive.c -o executive.o
gcc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.28\" -DNDEBUG -c judge.c -o judge.o
gcc -std=gnu99 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_XOPEN_SOURCE=600 -O2 -D_POSIX_C_SOURCE=200112L -Wall -pedantic-errors  -Wcast-align -Wpointer-arith -Wbad-function-cast -DVERSION=\"0.28\" -DNDEBUG -c linux.c -o linux.o
linux.c:23:43: error: attr/attributes.h: No such file or directory
linux.c: In function ‘set_ptime’:
linux.c:42: warning: implicit declaration of function ‘attr_setf’
linux.c:43: error: ‘ATTR_DONTFOLLOW’ undeclared (first use in this function)
linux.c:43: error: (Each undeclared identifier is reported only once
linux.c:43: error: for each function it appears in.)
linux.c: In function ‘get_ptime’:
linux.c:55: warning: implicit declaration of function ‘attr_getf’
linux.c:55: error: ‘ATTR_DONTFOLLOW’ undeclared (first use in this function)
make: *** [linux.o] Error 1

---

