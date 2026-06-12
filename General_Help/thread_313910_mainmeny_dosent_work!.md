---
title: "mainmeny dosent work!"
date: 2006-12-06
forum: General Help
---

### Post by larvar on 2006-12-06
hello! sorry for my bad english. im new to ubuntu, everything is working perfect. today was installing crossover office with photoshop successfully. then i was trying to install mountISO, but some error came up, and it did not install. well, now I have a strange problem. everytime I hit the mainmeny icon, the bugreport dialog comming up with this message (and the mainmeny do not work, nor the bottom panel):
[I]
  Memory status: size: 45056000 vsize: 0 resident: 45056000 share: 0 rss: 22892544 rss_rlim: 0
CPU usage: start_time: 1165446056 rtime: 0 utime: 449 stime: 0 cutime:436 cstime: 0 timeout: 13 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225771344 (LWP 14097)]
(no debugging symbols found)

(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75be323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eb61b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74a6770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74a7ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76c2122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76c2159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76c21d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b11d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b11dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b0d591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76b7aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76b9802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76bc7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76bcb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7abb574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225771344 (LWP 14097)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75be323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eb61b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74a6770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74a7ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76c2122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76c2159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76c21d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b11d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b11dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b0d591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76b7aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76b9802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76bc7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76bcb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7abb574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
[/I]
A clue, anyone?

---

