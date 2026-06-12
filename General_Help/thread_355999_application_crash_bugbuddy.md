---
title: "application crash bugbuddy"
date: 2007-02-07
forum: General Help
---

### Post by qpwoeiruty on 2007-02-07
I was trying to extract an archive (right-click/extract here) and bugbuddy popped up. Now, no matter what, the top and bottom bars no longer function and bugbuddy keeps popping up, even after a reboot.

```
Memory status: size: 31207424 vsize: 0 resident: 31207424 share: 0 rss: 12771328 rss_rlim: 0
CPU usage: start_time: 1170905220 rtime: 0 utime: 44 stime: 0 cutime:40 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225541968 (LWP 5358)]
(no debugging symbols found)
...
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75f1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eea1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74da770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74dbef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76f6122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76f6159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76f61d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b45d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b45dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b41591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76ebaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76ed802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76f07df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76f0b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7aef574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225541968 (LWP 5358)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75f1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eea1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74da770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74dbef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76f6122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76f6159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76f61d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b45d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b45dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b41591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76ebaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76ed802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76f07df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76f0b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7aef574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

I guess I'm really bad at search :-/
deleted .recently-used.xbel and it's ok

---

