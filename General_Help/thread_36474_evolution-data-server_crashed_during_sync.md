---
title: "evolution-data-server crashed during sync"
date: 2005-05-23
forum: General Help
---

### Post by brj on 2005-05-23
i finally managed to sync my palm tungste e with gnome-pilot and now the evolution-data-server crashes while processing the calendar.

the backtrace looks as follows:

Backtrace was generated from '/usr/libexec/evolution-data-server-1.2'

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1218535296 (LWP 10527)]
[New Thread -1230197840 (LWP 10533)]
[New Thread -1221805136 (LWP 10528)]
(no debugging symbols found)
...
(no debugging symbols found)
0xffffe410 in ?? ()
#0  0xffffe410 in ?? ()
#1  0xbffff2e4 in ?? ()
#2  0x00000000 in ?? ()
#3  0xbffff1a0 in ?? ()
#4  0xb76a347b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#5  0xb763c486 in system () from /lib/tls/i686/cmov/libc.so.6
#6  0xb763c217 in system () from /lib/tls/i686/cmov/libc.so.6
#7  0x0804b664 in server_logging_register_domain ()
#8  <signal handler called>
#9  0xb7d18b77 in pvl_head () from /usr/lib/libecal-1.2.so.2
#10 0xb7d03890 in icalcomponent_as_ical_string ()
   from /usr/lib/libecal-1.2.so.2
#11 0xb72dd416 in e_cal_backend_file_todos_get_type ()
   from /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
#12 0xb778da03 in g_child_watch_add () from /usr/lib/libglib-2.0.so.0
#13 0xb778ad0f in g_main_depth () from /usr/lib/libglib-2.0.so.0
#14 0xb778bcb5 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb778bfd7 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#16 0xb778c51e in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb79056f3 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#18 0x0804bd87 in main ()

Thread 3 (Thread -1221805136 (LWP 10528)):
#0  0xffffe410 in ?? ()
No symbol table info available.
#1  0xb72cb9d8 in ?? ()
No symbol table info available.
#2  0xffffffff in ?? ()
No symbol table info available.
#3  0x00000009 in ?? ()
No symbol table info available.
#4  0xb76c8549 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb778c8de in g_main_loop_get_context () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb778bf57 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb778c51e in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb787ff28 in link_thread_io_context () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#9  0xb77e3398 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb72cbad8 in ?? ()
No symbol table info available.
#11 0xb77a4362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#0  0xffffe410 in ?? ()

thanks jakob

---

