---
title: "Looping error, doesn't stop after several boots"
date: 2007-01-07
forum: General Help
---

### Post by Robert Leithe on 2007-01-07
I downloaded an .ISO, right clicked it and chose to expand it to my harddrive. Upon doing so, a crash ocurred, and a bug report (something I've never seen before in my relative short experience with Linux) was displayed. I clicked "Close" (as opposed to Save). A new crash ocurred, and the same dialog box came up. This went on about 5-6 times. And then I booted the computer (software initiated, not the kind where I simply hold the power button until "black out").

I logged back on, and the series of crashes began as if nothing had happened. This time I saved three of these logs, but chose Close a couple of times after that. Then I was presented my desktop. No menu at the top or toolbar at the bottom.

I pressed my power button shortly, and the usual shut down dialog appeared. I chose to shut down the computer. Powered it back on. Logged on, and - you guessed right. The same thing.

Thanks to my external USB-drives I am able to open what in Windows is referred to as Explorer windows (forgive my lack of Ubuntu terminology, I am, as I said, fairly new to this system). And from here I can run programs (such as Firefox, from which I am posting this request for assistance).

Any ideas as to how I can get back to normal?

Sincerely,

Here's a sample of the saved bug report:

********************** BUG REPORT START ****************
Memory status: size: 32657408 vsize: 0 resident: 32657408 share: 0 rss: 13520896 rss_rlim: 0
CPU usage: start_time: 1168115539 rtime: 0 utime: 41 stime: 0 cutime:37 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1224952144 (LWP 4822)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb7682323 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
#2 0xb7f7a1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3 <signal handler called>
#4 0xffffe410 in __kernel_vsyscall ()
#5 0xb756a770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6 0xb756bef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7 0xb7786122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8 0xb7786159 in g_log () from /usr/lib/libglib-2.0.so.0
#9 0xb77861d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bd5d5d in gtk_recent_info_get_short_name ()
from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bd5dba in gtk_recent_info_get_display_name ()
from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bd1591 in gtk_recent_chooser_menu_new ()
from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb777baa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb777d802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77807df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7780b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b7f574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1224952144 (LWP 4822)):
#0 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1 0xb7682323 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2 0xb7f7a1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3 <signal handler called>
No symbol table info available.
#4 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5 0xb756a770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6 0xb756bef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7 0xb7786122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8 0xb7786159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9 0xb77861d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bd5d5d in gtk_recent_info_get_short_name ()
from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bd5dba in gtk_recent_info_get_display_name ()
from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bd1591 in gtk_recent_chooser_menu_new ()
from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb777baa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb777d802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77807df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7780b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b7f574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0 0xffffe410 in __kernel_vsyscall ()
********************** BUG REPORT STOP ****************

---

### Post by KJS on 2007-01-07
Having the same problem...
renamed an img file (on an nfs share)  to iso and extracted the contents in the same directory with file-roller (large 4gb file)

somehow in connection with that event my gnome-panel started the incredible crash loop. Have been looking for solutions for an hour or so. Tried renaming the .gconf, .gconfd, .gnome .gnome2 folders to no avail
also tried renaming the panel folder found somewhere under the home directory

My girlfriends user works fine. Its only my account that is in trouble.

Never imagined finding someone whose gnome-panel problems started in connection with an iso file extraction. Mysterious

running ubuntu 64 bit by the way, sata 2 harddrive and athlon x2 proc

---

### Post by KJS on 2007-01-07
Found the solution

you need to delete the 
*.recently-used.xbel*
file found in your home directory

---

### Post by Robert Leithe on 2007-01-07
Thank you, thank you, thank you!

Sincerely

---

