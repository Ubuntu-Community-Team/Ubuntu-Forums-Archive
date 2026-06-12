---
title: "Can't get into Gnome on Edgy."
date: 2006-12-02
forum: General Help
---

### Post by saxmanlarry on 2006-12-02
Hey, I'm fairly new to Ubuntu (a couple months).

Over my Thanksgiving vacation, I decided to do a fresh install of Edgy. I loved it. After maybe two weeks of that:

I was copying some files off of a cd onto my desktop. It crashed, forced the system to reboot. Ever since, when I try to log in, Gnome goes through its normal splash screen. Then upon loading my desktop and trying to load the rest of the tool bars and such, it stops. "Bug Buddy" appears with a bug reporting tool. The system sits there and never finished start up. I've done a lot of work on the system already, I would rather not start from scratch.

I've run an FSCK on the disk with no effect. Beyond that, I'm not sure what I can do. I have KDE installed, trying to load it, it runs incredibly slowly.

```
Memory status: size: 73900032 vsize: 0 resident: 73900032 share: 0 rss: 13848576 rss_rlim: 0
CPU usage: start_time: 1165090476 rtime: 0 utime: 180 stime: 0 cutime:166 cstime: 0 timeout: 14 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
#repeats omitted
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225115984 (LWP 4711)]
(no debugging symbols found)
#repeats omitted
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb765a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f521b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7542770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7543ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb775e122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb775e159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb775e1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7badd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7baddba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7ba9591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7753aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7755802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77587df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7758b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b57574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225115984 (LWP 4711)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb765a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f521b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7542770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7543ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb775e122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb775e159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb775e1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7badd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7baddba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7ba9591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7753aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7755802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77587df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7758b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b57574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

Any help would be amazing wonderful.
Thanks,

-Larry

---

### Post by Peter76 on 2006-12-02
Hi, this is a bug in Edgy (already reported) Hit alt+f1, login, and do:

rm .recently-used.xbel

And you should be fine.

Good luck, peter

---

### Post by saxmanlarry on 2006-12-02
Thank you so much!

Fixed it perfectly. Sorry, I apparently didn't spend enough time searching myself. 

Thanks again,

-Larry

---

