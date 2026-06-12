---
title: "Gnome in death-loop"
date: 2006-11-17
forum: General Help
---

### Post by Aerugo on 2006-11-17
Hi!

I just ended up with a big mess after trying to extract the contents of a ISO-file. I was running firefox, rhythmbox and terminal when it happened. I got a "bug feedback" after trying to right-click extract the contents of an ISO with seemingly no appearant results. When I pressed "close" my gnome panels seemed to reaload, appear again, and then throw the same bug feedback agent window back at me. I could not interact with gnome at all. I tried to ctrl-alt-backspace, but when I logged back in the problem was still there, the panels freezing the second i logged in. I tried failsafe mode, but that didn't help either.

I'm writing this from a failsafe terminal. I'm running Edgy.

One last thing. Come to think of it; I tried to mount the ISO a few moments earlier. It didn't work; nothing showed up and the ISO wouldn't mount. I have actually never been able to mount an ISO on my system. Anyway, it just struck me: I left the operation half done the last time i tried it, right before I did the whole doom bringing extraction. I think the last thing I executed in terminal was "sudo modprobe loop".

This is what showed up in the bug feedback agent:

```
Memory status: size: 34025472 vsize: 0 resident: 34025472 share: 0 rss: 16486400 rss_rlim: 0
CPU usage: start_time: 1163782512 rtime: 0 utime: 78 stime: 0 cutime:74 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1225038160 (LWP 5759)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb766c323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f641b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7554770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7555ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7770122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7770159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77701d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bbfd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bbfdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bbb591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7765aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7767802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb776a7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb776ab89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b69574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225038160 (LWP 5759)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb766c323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f641b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7554770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7555ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7770122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7770159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77701d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bbfd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bbfdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bbb591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7765aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7767802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb776a7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb776ab89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b69574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

Keep in mind that I'm a beginner, fresh out of windows. Just learning how to handle command-line.

---

### Post by Aerugo on 2006-11-17
Found the solution in a previous post! :)

[http://ubuntuforums.org/showthread.php?t=289154](http://ubuntuforums.org/showthread.php?t=289154)

Made more clear for noobs like me that have to figure out how to delete in terminal and don't really know what the ~ sign means ;)

This is what I typed into terminal:

```
sudo rm -f /home/"user"/.recently-used.xbel
```

That's it.

---

