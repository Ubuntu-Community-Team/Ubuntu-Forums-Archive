---
title: "Help installing Dionaea honeypot"
date: 2013-10-31
forum: General Help
---

### Post by The Quizmaster on 2013-10-31
Hey, how's everybody doing? I recently installed Ubuntu 13.04 a few months and am trying to setup a Dionaea honeypot. I followed all of the compilation instructions at [http://dionaea.carnivore.it](http://dionaea.carnivore.it) The ./configure script appeared to be working ok, and when I finally make && make install, I get the following errors:```
 root@Enigma:~/dionaea# make
make  all-recursive
make[1]: Entering directory `/root/dionaea'
Making all in src
make[2]: Entering directory `/root/dionaea/src'
gcc -DHAVE_CONFIG_H -I. -I..    -I/opt/dionaea/include -DEV_COMPAT3=0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I/opt/dionaea/include/  -I/opt/dionaea/include/  -I../include -I .. -fno-strict-aliasing -std=c99 -D_GNU_SOURCE -D_GNU_SOURCE -I/opt/dionaea/include -DEV_COMPAT3=0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I/opt/dionaea/include/ -Wall -Werror -Wstrict-prototypes -g  -MT dionaea-dionaea.o -MD -MP -MF .deps/dionaea-dionaea.Tpo -c -o dionaea-dionaea.o `test -f 'dionaea.c' || echo './'`dionaea.c
dionaea.c: In function &#8216;main&#8217;:
dionaea.c:686:3: error: &#8216;g_thread_init&#8217; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:260) [-Werror=deprecated-declarations]
dionaea.c:689:2: error: &#8216;g_mutex_new&#8217; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:272) [-Werror=deprecated-declarations]
cc1: all warnings being treated as errors
make[2]: *** [dionaea-dionaea.o] Error 1
make[2]: Leaving directory `/root/dionaea/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/dionaea'
make: *** [all] Error 2
root@Enigma:~/dionaea# make install
Making install in src
make[1]: Entering directory `/root/dionaea/src'
gcc -DHAVE_CONFIG_H -I. -I..    -I/opt/dionaea/include -DEV_COMPAT3=0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I/opt/dionaea/include/  -I/opt/dionaea/include/  -I../include -I .. -fno-strict-aliasing -std=c99 -D_GNU_SOURCE -D_GNU_SOURCE -I/opt/dionaea/include -DEV_COMPAT3=0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I/opt/dionaea/include/ -Wall -Werror -Wstrict-prototypes -g  -MT dionaea-dionaea.o -MD -MP -MF .deps/dionaea-dionaea.Tpo -c -o dionaea-dionaea.o `test -f 'dionaea.c' || echo './'`dionaea.c
dionaea.c: In function &#8216;main&#8217;:
dionaea.c:686:3: error: &#8216;g_thread_init&#8217; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:260) [-Werror=deprecated-declarations]
dionaea.c:689:2: error: &#8216;g_mutex_new&#8217; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:272) [-Werror=deprecated-declarations]
cc1: all warnings being treated as errors
make[1]: *** [dionaea-dionaea.o] Error 1
make[1]: Leaving directory `/root/dionaea/src'
make: *** [install-recursive] Error 1 
```
How can I fix this so I can install Dionaea, I really need it for a computer science project?

---

### Post by The Quizmaster on 2013-10-31
Could it be a dependency issue with Python 3.2, I don't know, what do you guys think I need to do to install it correctly, please help me out?

---

