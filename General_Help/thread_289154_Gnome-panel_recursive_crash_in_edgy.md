---
title: "Gnome-panel recursive crash in edgy"
date: 2006-10-30
forum: General Help
---

### Post by jdralphs on 2006-10-30
I've been using edgy for about a week now and today, after attempting to extract an iso in my /home directory -- gnome-panel decided to recursively crash on me.  Here is the output from bug buddy.  Anyone know how to fix this?

> Memory status: size: 54538240 vsize: 0 resident: 54538240 share: 0 rss: 14458880 rss_rlim: 0
CPU usage: start_time: 1162246242 rtime: 0 utime: 153 stime: 0 cutime:147 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

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
[New Thread -1225779536 (LWP 4850)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb75b6323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eaf1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb749f770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74a0ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76bb122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76bb159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76bb1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b0ad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b0adba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b06591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76b0aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76b2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76b57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76b5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ab4574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225779536 (LWP 4850)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75b6323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eaf1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb749f770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74a0ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76bb122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76bb159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76bb1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b0ad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b0adba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b06591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76b0aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76b2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76b57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76b5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ab4574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by DeMonk on 2006-10-31
I got the exact same problem, after extracting an .iso file gnome-panel crashes again and again even after restart


> Memory status: size: 40419328 vsize: 0 resident: 40419328 share: 0 rss: 16052224 rss_rlim: 0
CPU usage: start_time: 1162286188 rtime: 0 utime: 35 stime: 0 cutime:32 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1225607504 (LWP 21813)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75e1323 in __waitpid_nocancel ()
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
#18 0x08061d8c in main (argc=5, argv=0xbfaffed4) at main.c:95

Thread 1 (Thread -1225607504 (LWP 21813)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75e1323 in __waitpid_nocancel ()
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
#18 0x08061d8c in main (argc=5, argv=0xbfaffed4) at main.c:95
	context = <value optimized out>
	program = (GnomeProgram *) 0x80c9028
#0  0xffffe410 in __kernel_vsyscall ()


---

### Post by siman on 2006-11-14
update: found bug report.. has a workaround, see here: [https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/66189](https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/66189). deleting ~/.recently-used.xbel did the trick for me.

same problem here, gnome-panel crashes, "bug buddy" pops up again the moment i close it.

I also extracted an iso (not in my home dir) before this happend - wouldn't have thought thats related

```


Memory status: size: 84111360 vsize: 0 resident: 84111360 share: 0 rss: 14557184 rss_rlim: 0
CPU usage: start_time: 1163522216 rtime: 0 utime: 101 stime: 0 cutime:97 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1225058640 (LWP 21528)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7667323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f5f1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb754f770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7550ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb776b122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb776b159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb776b1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bbad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bbadba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bb6591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7760aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7762802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77657df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7765b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b64574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225058640 (LWP 21528)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7667323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f5f1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb754f770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7550ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb776b122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb776b159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb776b1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bbad5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bbadba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bb6591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7760aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7762802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77657df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7765b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b64574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


```

---

### Post by lognok on 2006-11-15
Deleting ~/.recently-used.xbel also did the trick for me.

---

### Post by FredSambo on 2006-11-21
same problem here.

phew. thanks!

---

### Post by rjz35 on 2006-11-21
Deleting ~/.recently-used.xbel also did the trick for me.

thx

---

### Post by FredSambo on 2006-11-21
FWIW i actuall had to delete ~/.recently-used as well as ~/.recently-used.xbel

---

### Post by el_itur on 2007-01-11
I've found this problem, but only when I run compiz. It crashes suddenly when I try to do anything to the panel. Any clue?

---

### Post by andoty_jazz on 2007-01-11
hey... guys.

I got this problem too this very hour. 

Just fixed the problem because of the workaround.

Thank you so mch.

;)

---

### Post by jkeyes0 on 2007-02-28
Thank God for you guys. I was extracting the contents of an ISO I had just created when this bug occurred. Removing .recently-used.xbel fixed it for me.

---

### Post by zami on 2007-03-21
I had this exact problem last night, also after trying to extract a .iso file.

(I half expected an error, but not the Bug-Buddy infinite loop!)

I also solved it by removing the .recently-used.xbel - thank goodness for these forums!!

I did
CTRL+ALT+BACKSPACE,
clicked Options and Choose Session,
chose Failsafe Terminal and logged in
ran
```

sudo rm -f /home/"user"/.recently-used.xbel

```
then CTRL+ALT+BACKSPACE again and logged in as normal.

I read some other posts with people pulling up a terminal on their desktop, but that wasn't an option for me.  NOTHING but CTRL+ALT+BACKSPACE was responsive during the Bug-Buddy loop.

-zami

---

### Post by CocoAUS on 2007-03-21
I wish I'd known about the workaround when this happened to me!  I reinstalled Edgy, then the panel crashed before I was even done install programs and codecs, so I installed Fedora 7, downloaded Feisty Heard 5, burned it, and install Feisty.  I'm happy with Feisty, but geez...the workaround would've made my life so much easier!

---

### Post by sgusto on 2007-03-23
I had the same problem and was glad to find the solution here  (rm -rf .recently-used.xbel).
Thank you Sebastien Bacher
 
It happened the same way - extracting an iso file.  The iso file was on another partition and might have been corrupted.  It was a DVD iso and ended with  '.iso.iso'  instead of just one.   Don't know if all that had anything to do with it or not. 

best
S

---

