---
title: "Ubuntu freaks out on login"
date: 2007-03-20
forum: General Help
---

### Post by Eindringling on 2007-03-20
For some reason when I log in a bunch of things come up (gaim, terminal, home folder) and I can't use my keyboard on them. I have to close them, and once I do that my keyboard works. So, that wouldn't be too much of a problem, except firefox and gaim have started to randomly close. When I go into system>preferences, none of the icons load and i get the following error report:

```

Memory status: size: 59543552 vsize: 0 resident: 59543552 share: 0 rss: 17973248 rss_rlim: 0
CPU usage: start_time: 1174373725 rtime: 0 utime: 157 stime: 0 cutime:138 cstime: 0 timeout: 19 it_real_value: 0 frequency: 0

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
[New Thread -1225234768 (LWP 25712)]
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
#1  0xb763d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f351b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb75686a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7b03292 in _gtk_icon_cache_add_icons ()
   from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7b03537 in _gtk_icon_cache_get_icon_flags ()
   from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7b08bf3 in gtk_icon_info_get_type () from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7b09e92 in gtk_icon_theme_lookup_icon ()
   from /usr/lib/libgtk-x11-2.0.so.0
#9  0x080765f7 in panel_find_icon ()
#10 0x0807e5d8 in panel_make_menu_icon ()
#11 0x0807ea68 in panel_make_menu_icon ()
#12 0xb7736aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#13 0xb7738802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#14 0xb773b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#15 0xb773bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#16 0xb7b3a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x08061d8c in main ()

Thread 1 (Thread -1225234768 (LWP 25712)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb763d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f351b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb75686a8 in strcmp () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb7b03292 in _gtk_icon_cache_add_icons ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7b03537 in _gtk_icon_cache_get_icon_flags ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7b08bf3 in gtk_icon_info_get_type () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7b09e92 in gtk_icon_theme_lookup_icon ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0x080765f7 in panel_find_icon ()
No symbol table info available.
#10 0x0807e5d8 in panel_make_menu_icon ()
No symbol table info available.
#11 0x0807ea68 in panel_make_menu_icon ()
No symbol table info available.
#12 0xb7736aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0xb7738802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb773b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb773bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7b3a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#17 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

I'm sort of new to linux, so I have no clue how to fix this, and I dont really know what to make of the error report, so any possible help would be much appreciated.

btw, everything works fine when i log into with failsafe gnome (which is what I'm using right now, otherwise firefox probably would have closed out by now)

thanks

---

