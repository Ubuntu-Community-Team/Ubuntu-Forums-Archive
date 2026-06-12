---
title: "Gnome keeps crashing!"
date: 2006-12-12
forum: General Help
---

### Post by Kittie Rose on 2006-12-12
I can't access either of the menu bars! It crashed with the following message:

Memory status: size: 32448512 vsize: 0 resident: 32448512 share: 0 rss: 14495744 rss_rlim: 0
CPU usage: start_time: 1165966488 rtime: 0 utime: 75 stime: 0 cutime:71 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1225611600 (LWP 5008)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb75e0323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ed91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74c9770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74caef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76e5122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76e5159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76e51d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b34d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b34dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b30591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76daaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76dc802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76df7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76dfb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ade574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225611600 (LWP 5008)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75e0323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ed91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74c9770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74caef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76e5122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76e5159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76e51d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b34d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b34dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b30591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76daaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76dc802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76df7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76dfb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ade574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by wpshooter on 2006-12-12
When did this start ?  Have you been running Ubuntu sucessfully prior to this happening or is this a completely or fairly new installation ?

---

### Post by Kittie Rose on 2006-12-12
Yes, Ubuntu was working fine until I got these errors. Well, by fine I mean I still got other kinds of ridiculous errors I shouldn't have gotten. I can't use it at all now.

Is Edgy just generally unstable?

---

### Post by wpshooter on 2006-12-12
Well I have only used Edgy experimentally.  My advise would be to go back to Dapper 6.06.1.

3 - things.

Make sure that you burn your downloaded ISO to your CD at 4X or less.

Make sure that you check the integrity of your CD by running the verification function found on the initial Ubunut boot screen menu.

Check your computer's memory by running the memtest.

Of course, the hardware specs. of your computer will greatly determine wheather you want to install from the DESKTOP (live CD) or the ALTERNATE CD.

Good luck.

---

### Post by maxamillion on 2006-12-12
Also, before burning the image check the md5sum to ensure the disk downloaded correctly.

/me

---

### Post by Kittie Rose on 2006-12-12
??? What's all this about burning? How does that help me get Gnome working...

---

### Post by JohnBoy55 on 2006-12-12
What they're trying to say is that you need to ensure that your downloaded Ubuntu cd image was downloaded accurately, i.e., with no data transmission errors.

---

### Post by Kittie Rose on 2006-12-12
[http://ubuntuforums.org/showthread.php?t=296823](http://ubuntuforums.org/showthread.php?t=296823)

Found the answer!!! 

removing recently-used.xbel seems to solve a whole host of problems...

as does sudo dpkg -reconfigure xserver-xorg (my X system went down on me once).

Someone should sticky that! If you Linicks is ****** up, try the first, then the second...

---

### Post by zanglang on 2006-12-12
Phew, thanks for the solution, just deleting the .xbel file did the trick. :D

---

