---
title: "What does this mean? (Bug Buddy question)"
date: 2007-04-27
forum: General Help
---

### Post by spotdog14 on 2007-04-27
Hello everyone, i have been registered in this forum for a while, but dont really post because i can usually find my answers by searching. But recently i keep getting this bug buddy report about Evolution crashing or something to that extent. Here is the report:

Memory status: size: 1695744 vsize: 0 resident: 1695744 share: 0 rss: 483328 rss_rlim: 0
CPU usage: start_time: 1177682795 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-data-server-1.8'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e8374e in wait4 () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e83727 in wait3 () from /lib/tls/i686/cmov/libc.so.6
#3  0x0804ed62 in ?? ()
#4  0xbf943290 in ?? ()
#5  0x00000000 in ?? ()


What does it mean, and what can i do to fix it? I am running Edgy with all the updates on an Asus S5n laptop. Thanks for any help guys!

---

### Post by spotdog14 on 2007-04-28
bump

---

### Post by jpeddicord on 2007-04-28
That usually reflects a bug in the program. If it keeps happening, make sure that you file a bug when it asks you to. It only takes a few clicks, and it will email you with bug updates.

Jacob

---

