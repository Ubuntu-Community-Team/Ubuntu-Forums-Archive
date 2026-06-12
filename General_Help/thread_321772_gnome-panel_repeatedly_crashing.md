---
title: "gnome-panel repeatedly crashing"
date: 2006-12-19
forum: General Help
---

### Post by Pitbull11188 on 2006-12-19
My gnome-panel keeps crashing whenever I use gnome. Right now I am typing this from fluxbox b/c whenever I boot up using gnome it shows me a bugzilla report, and then when I exit the report it comes right back up. This has rendered my computer unusable when attempting to use gnome. Here is the error information:

Memory status: size: 31911936 vsize: 0 resident: 31911936 share: 0 rss: 13434880 rss_rlim: 0
CPU usage: start_time: 1166542131 rtime: 0 utime: 44 stime: 0 cutime:43 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0

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
[New Thread -1225845072 (LWP 5097)]
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
#1  0xb75a8323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7490770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7491ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76ac122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76ac159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76ac1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7afbd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7afbdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7af7591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76a1aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76a3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76a67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76a6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7aa5574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225845072 (LWP 5097)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75a8323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ea01b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7490770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7491ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76ac122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76ac159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76ac1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7afbd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7afbdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7af7591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76a1aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76a3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76a67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76a6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7aa5574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by doggie on 2006-12-20
I have the same problem.... do you have beryl installed??, I do, i guess that's why i'm getting all those problems with gnome-panel, If you find the answer, please let me know :-k  :-k

---

### Post by mts-fi on 2007-01-09
I had the same problem...

solution:
delete (or rename) the
.recently-used.xbel (It's hidden, press Ctrl+h to see it)
file found in your home directory

I found it from:
[http://ubuntuforums.org/showthread.php?t=316356](http://ubuntuforums.org/showthread.php?t=316356)

See also:
[http://bugzilla.gnome.org/show_bug.cgi?id=358044](http://bugzilla.gnome.org/show_bug.cgi?id=358044)

---

