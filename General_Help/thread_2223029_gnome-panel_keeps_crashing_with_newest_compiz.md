---
title: "gnome-panel keeps crashing with newest compiz"
date: 2014-05-09
forum: General Help
---

### Post by lpm11 on 2014-05-09
Hi!

I have installed Ubuntu 14.04 LTS. Than, I installed gnome-panel, compizconfig-settings-manager and compiz-plugins. Next, removed unity. I did apt-get upgrade, rebooted and I have a login screen. When I choose gnome-classic with Metacity; everything is OKay.

When I choose gnome-classic with Compiz, I have problem - gnome-panel is crashing. After manual restarting it - I don't have some panels (networking, menu to logout, clock etc.). And here comes the gdb log:

```
(gdb) run /usr/bin/gnome-panel
Starting program: /usr/bin/gnome-panel /usr/bin/gnome-panel
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
[New Thread 0xb6585b40 (LWP 2738)]
[New Thread 0xb5bbfb40 (LWP 2739)]
[New Thread 0xb13d9b40 (LWP 2740)]
[New Thread 0xb09ffb40 (LWP 2741)]
*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug


(gnome-panel:2734): Gtk-WARNING **: no parent (nil) is not realized but child GtkPlug 0x83b4510 is realized

(gnome-panel:2734): Gtk-WARNING **: no parent (nil) is not realized but child GtkPlug 0x83b4398 is realized

(gnome-panel:2734): Gtk-WARNING **: no parent (nil) is not realized but child GtkPlug 0x83b4220 is realized

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_set_background_rgba: assertion 'GDK_IS_WINDOW (window)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_get_display: assertion 'GDK_IS_WINDOW (window)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_display_sync: assertion 'GDK_IS_DISPLAY (display)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_get_user_data: assertion 'GDK_IS_WINDOW (window)' failed

** (gnome-panel:2734): CRITICAL **: panel_widget_background_changed: assertion 'PANEL_IS_WIDGET (panel)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_set_background_rgba: assertion 'GDK_IS_WINDOW (window)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_get_display: assertion 'GDK_IS_WINDOW (window)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_display_sync: assertion 'GDK_IS_DISPLAY (display)' failed

(gnome-panel:2734): Gdk-CRITICAL **: gdk_window_get_user_data: assertion 'GDK_IS_WINDOW (window)' failed

** (gnome-panel:2734): CRITICAL **: panel_widget_background_changed: assertion 'PANEL_IS_WIDGET (panel)' failed

Program received signal SIGSEGV, Segmentation fault.
0xb75c6022 in g_type_check_instance_cast ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
(gdb) x/10x $sp
0xbfffea10:	0xb7766000	0xb5c06d78	0xbfffea30	0xb76a3cf1
0xbfffea20:	0xb5c06d78	0xb5c06d78	0x083aef91	0xb7594000
0xbfffea30:	0x083ba4f0	0x083aef91
(gdb) backtrace
#0  0xb75c6022 in g_type_check_instance_cast ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#1  0xb1615366 in ?? () from /usr/lib/gnome-panel/4.0/libwnck-applet.so
#2  0xb1615513 in ?? () from /usr/lib/gnome-panel/4.0/libwnck-applet.so
#3  0xb75a5321 in g_cclosure_marshal_VOID__STRINGv ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#4  0xb75a2cce in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#5  0xb75bc080 in g_signal_emit_valist ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#6  0xb75bcbf3 in g_signal_emit ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#7  0xb76a2340 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#8  0xb6b2b3c6 in ffi_call_SYSV () from /usr/lib/i386-linux-gnu/libffi.so.6
#9  0xb6b2b14b in ffi_call () from /usr/lib/i386-linux-gnu/libffi.so.6
#10 0xb75a3671 in g_cclosure_marshal_generic_va ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#11 0xb75a1457 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#12 0xb75a2cce in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#13 0xb75bc080 in g_signal_emit_valist ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#14 0xb75bcbf3 in g_signal_emit ()
   from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
#15 0xb76a2c60 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
---Type <return> to continue, or q <return> to quit--- 
#16 0xb769cf88 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#17 0xb74ccc50 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#18 0xb74d00a7 in g_main_context_dispatch ()
   from /lib/i386-linux-gnu/libglib-2.0.so.0
#19 0xb74d0468 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#20 0xb74d076b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#21 0xb7bc680d in gtk_main () from /usr/lib/i386-linux-gnu/libgtk-3.so.0
#22 0x080625f5 in ?? ()
#23 0xb6f6ba83 in __libc_start_main (main=0x8062480, argc=2, argv=0xbffff204, 
    init=0x80ade00, fini=0x80ade70, rtld_fini=0xb7fed180 <_dl_fini>, 
    stack_end=0xbffff1fc) at libc-start.c:287
#24 0x08062697 in ?? ()
(gdb) 


```

Sometimes I start metacity, and than run compiz it is Okay. My machine is QEMU, but it happens on Virtualbox and seems to be software problem.
One more thing - the problem didn't happen before the 'apt-get upgrade'. There is a bug described here [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1232299) . It seems that previous version (1:0.9.11+14.04.20140409-0ubuntu1) was working correctly - I didn't have this problem.

Can you help me what to do?

---

