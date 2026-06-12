---
title: "Panel Crash After Doing Updates"
date: 2006-12-22
forum: General Help
---

### Post by tanman on 2006-12-22
I hope some one can point me in the right direction. I am having problems after I updated last night.
I normally have the menu Icon in the top panel where I click on it and then it drops down to give me the options of places, ad, preferences and so on. When I click on it now I get a bug report that says is unknown. So I opened up the properties of the top panel and got rid of that Icon and went back to the default when it has the 3 categories listed separately. The problem is now the bug report keeps coming up every time I close the report and I can not open anything on either the top or bottom panel. I can not even open up properties or anything. The only thing I can open are desk top icons.
Is there a way I can open up the terminal manually and try to uninstall the updates or something.
Thanks for any help.

---

### Post by tanman on 2006-12-22
Well I have been playing with the panels and can not getanything to work. I can not even shut down he computer properly for even that I con on the panel is frozen.
Now that I have applications, and etc at the top instaed of just the menu icon I can not get the 
bug report to disappear. Here is the report I am getting

Memory status: size: 41984000 vsize: 0 resident: 41984000 share: 0 rss: 19587072 rss_rlim: 0
CPU usage: start_time: 1166828314 rtime: 0 utime: 89 stime: 0 cutime:85 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1224948048 (LWP 5359)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7683323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f7b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb756b770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb756cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7787122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7787159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77871d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bd6d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bd6dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bd2591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb777caa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb777e802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77817df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7781b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b80574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1224948048 (LWP 5359)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7683323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f7b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb756b770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb756cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7787122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7787159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77871d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bd6d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bd6dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bd2591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb777caa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb777e802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77817df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7781b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b80574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

I have no idea what any of this means but I have to use my lap top to post on the forums for all my application launchers are on the panel.

Does this have re-install written all over it? Or can I go back in time.
Thanks for any suggestions.

---

