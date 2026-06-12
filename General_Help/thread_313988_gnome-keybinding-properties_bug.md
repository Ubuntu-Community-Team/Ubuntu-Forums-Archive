---
title: "gnome-keybinding-properties bug???"
date: 2006-12-06
forum: General Help
---

### Post by jaywhy13 on 2006-12-06
Sometimes while running Gnome (I have Kubuntu... installed Gnome) I get the following bug buddy when I try to open the keyboard shortcuts dialog. I'm also running Xgl, Alt+F2 doesn't work either. 

Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 37818368 vsize: 0 resident: 37818368 share: 0 rss: 11915264 rss_rlim: 0
CPU usage: start_time: 1165457971 rtime: 0 utime: 47 stime: 0 cutime:44 cstime: 0 timeout: 3 it_real_value: 0 frequency: 6

Backtrace was generated from '/usr/bin/gnome-keybinding-properties'

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
[Thread debugging using libthread_db enabled]
[New Thread -1225205568 (LWP 27236)]
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
#1  0xb787b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f261b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb6e27a7c in ?? ()
#5  0xb7b2b021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
#6  0xb7b2c78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb7b2e3bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb7b2e7bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb78c5802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb78c87df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb78c8b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb7ca5574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x0804dff8 in ?? ()
#14 0x080a1000 in ?? ()
#15 0x080531bc in _IO_stdin_used ()
#16 0x0804bf94 in g_object_ref@plt ()
#17 0x00000000 in ?? ()

Thread 1 (Thread -1225205568 (LWP 27236)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb787b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f261b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb6e27a7c in ?? ()
No symbol table info available.
#5  0xb7b2b021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#6  0xb7b2c78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0xb7b2e3bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0xb7b2e7bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#9  0xb78c5802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb78c87df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb78c8b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7ca5574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x0804dff8 in ?? ()
No symbol table info available.
#14 0x080a1000 in ?? ()
No symbol table info available.
#15 0x080531bc in _IO_stdin_used ()
No symbol table info available.
#16 0x0804bf94 in g_object_ref@plt ()
No symbol table info available.
#17 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

