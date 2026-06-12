---
title: "Gnome-panel bug"
date: 2006-12-22
forum: General Help
---

### Post by Aurdal on 2006-12-22
Gnome panel doesn't feel too good:
[IMG]http://i106.photobucket.com/albums/m264/kaurdal/Screenshot-BugBuddy.png[/IMG]

Here's the full error:
```

Memory status: size: 54710272 vsize: 0 resident: 54710272 share: 0 rss: 13996032 rss_rlim: 0
CPU usage: start_time: 1166809833 rtime: 0 utime: 136 stime: 0 cutime:126 cstime: 0 timeout: 10 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225652560 (LWP 4606)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75d7323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ecf1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74bf770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74c0ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76db122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76db159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76db1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b2ad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b2adba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b26591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76d0aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76d2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76d57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76d5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ad4574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225652560 (LWP 4606)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75d7323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ecf1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74bf770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74c0ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76db122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76db159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76db1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b2ad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b2adba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b26591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76d0aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76d2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76d57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76d5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ad4574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

The only thing I can think of that I've done which could have caused this is that I opened the "menu editor" (Alcarte I think it's called) and unchecked the "Take Screenshot" in the Accessories menu. I've tried restarting Gnome-Panel, gdm, even the whole computer, but to no avail. Any help would be greatly appreciated.

Thanks.
-Kristoffer

---

### Post by Peter76 on 2006-12-22
If you mean that every time you try to start up your desktop you only get a bug-buddy window and nothing else happens, switch to another console ( ctrl+f1 ), login and

rm .recently-used.xbel

There is a bug posted about this, but no solution yet.

Good luck

---

### Post by Aurdal on 2006-12-22
Thanks, that did the trick. :D

---

