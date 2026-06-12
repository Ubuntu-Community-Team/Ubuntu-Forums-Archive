---
title: "shall i report a bug? mail-notification crashes!"
date: 2005-04-04
forum: General Help
---

### Post by arctic on 2005-04-04
I hope this one wasn't already detected. At least a search gave no result:

System: Ubuntu 5.04 Hoary, i386

Description: When running the mail-notification tool for the Gnome-panel and running multiple mail accounts (3+), it severely crashes insted of retreiving information on incoming e-mails. It was tested with one normal pop account and two gmail accounts and only after adding a second gmail account it began to crash. Reactivation of the notifier during the session results in repeated crashes.

Reproduction: Reinstall of application and reboot of system does not change anything, crashes after every reboot and system login.

Bug-buddy output:

Backtrace was generated from '/usr/bin/mail-notification'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1223130464 (LWP 6917)]
[New Thread -1234113616 (LWP 6924)]
[New Thread -1268319312 (LWP 6923)]
[New Thread -1259926608 (LWP 6922)]
[New Thread -1251533904 (LWP 6921)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb78d125b in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb78ce690 in _L_mutex_lock_26 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0x080c51ac in ?? ()
#4  0x00000002 in ?? ()
#5  0xbffff868 in ?? ()
#6  0x080b98e0 in ?? ()
#7  0xb78b61c4 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#8  0x080c5160 in ?? ()
#9  0xbffff838 in ?? ()
#10 0xb784d09f in gdk_threads_leave () from /usr/lib/libgdk-x11-2.0.so.0
#11 0xb784d09f in gdk_threads_leave () from /usr/lib/libgdk-x11-2.0.so.0
#12 0xb7878412 in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#13 0xb769da0f in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#14 0xb769df74 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb769e51e in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#16 0xb7af6cc3 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x08078141 in main ()

Thread 5 (Thread -1251533904 (LWP 6921)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb78d125b in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78ce690 in _L_mutex_lock_26 () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#3  0x0000c6f0 in ?? ()
No symbol table info available.
#4  0x00000008 in ?? ()
No symbol table info available.
#5  0x08260910 in ?? ()
No symbol table info available.
#6  0xb76f5398 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb78b61c4 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0x0824d238 in ?? ()
No symbol table info available.
#9  0xb5671868 in ?? ()
No symbol table info available.
#10 0xb784d09f in gdk_threads_leave () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#11 0xb784d09f in gdk_threads_leave () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#12 0x08057897 in mn_pop3_mailbox_get_type ()
No symbol table info available.
#13 0x08071c98 in mn_client_session_run ()
No symbol table info available.
#14 0x08071d95 in mn_client_session_run ()
No symbol table info available.
#15 0x08071773 in mn_client_session_run ()
No symbol table info available.
#16 0x08057d57 in mn_pop3_mailbox_get_type ()
No symbol table info available.
#17 0xb76b6362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#18 0xb78ccae0 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#19 0xb7519c9a in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 4 (Thread -1259926608 (LWP 6922)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7513901 in select () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb73b3135 in _XPollfdCacheDel () from /usr/X11R6/lib/libX11.so.6
No symbol table info available.
#3  0xb73b3f89 in _XRead () from /usr/X11R6/lib/libX11.so.6
No symbol table info available.
#4  0xb73b4a24 in _XReply () from /usr/X11R6/lib/libX11.so.6
No symbol table info available.
#5  0xb73b0356 in XSync () from /usr/X11R6/lib/libX11.so.6
No symbol table info available.
#6  0xb7878853 in gdk_flush () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0x0805ec61 in mn_gmail_mailbox_get_type ()
No symbol table info available.
#8  0xb76b6362 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb78ccae0 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#10 0xb7519c9a in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 3 (Thread -1268319312 (LWP 6923)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb78d248b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f10d97 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb746f175 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74707d8 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb466f4c0 in ?? ()
No symbol table info available.
#8  0x00000000 in ?? ()
No symbol table info available.
#9  0x00000020 in ?? ()
No symbol table info available.
#10 0x00000000 in ?? ()
No symbol table info available.
#11 0x00000000 in ?? ()
No symbol table info available.
#12 0x00000000 in ?? ()
No symbol table info available.
#13 0x00000000 in ?? ()
No symbol table info available.
#14 0x00000000 in ?? ()
No symbol table info available.
#15 0x00000000 in ?? ()
No symbol table info available.
#16 0x00000000 in ?? ()
No symbol table info available.
#17 0x00000000 in ?? ()
No symbol table info available.
#18 0x00000000 in ?? ()
No symbol table info available.
#19 0x00000000 in ?? ()
No symbol table info available.
#20 0x00000000 in ?? ()
No symbol table info available.
#21 0x00000000 in ?? ()
No symbol table info available.
#22 0x00000000 in ?? ()
No symbol table info available.
#23 0x00000000 in ?? ()
No symbol table info available.
#24 0x00000000 in ?? ()
No symbol table info available.
#25 0x00000000 in ?? ()
No symbol table info available.
#26 0x00000000 in ?? ()
No symbol table info available.
#27 0x00000000 in ?? ()
No symbol table info available.
#28 0x00000000 in ?? ()
No symbol table info available.
#29 0x00000000 in ?? ()
No symbol table info available.
#30 0x00000000 in ?? ()
No symbol table info available.
#31 0x00000000 in ?? ()
No symbol table info available.
#32 0x00000000 in ?? ()
No symbol table info available.
#33 0x00000000 in ?? ()
No symbol table info available.
#34 0x00000000 in ?? ()
No symbol table info available.
#35 0x00000000 in ?? ()
No symbol table info available.
#36 0x00000000 in ?? ()
No symbol table info available.
#37 0x00000000 in ?? ()
No symbol table info available.
#38 0x00000000 in ?? ()
No symbol table info available.
#39 0x00000000 in ?? ()
No symbol table info available.
#40 0x00000000 in ?? ()
No symbol table info available.
#41 0xb74b2307 in _IO_file_write () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

anyone got an idea how to fix this? or should i report via bugzilla? :-s

---

### Post by arctic on 2005-04-05
no opinion from anyone? boy... i was hoping for a better response. especially from our linux-veterans...:-?

---

### Post by arctic on 2005-04-06
okay, i found a halfway decent answer to my problem, although it won't solve it. as it turns out, the app has always had problems with handling gmail accounts. the creator is trying to fix the issue but he seems to have trouble to make the gmail-account checking stable. so we will have to wait for future versions.

---

### Post by justaguynpc on 2005-04-07
Are there any other programs that do work (correctly) that are similiar to mail-notificaion?  I am unsure whether mail-notification was actually crashing, or whether my attempt at set-up was erred.  I attempted to set up multiple accounts, tested by sending e-mails back and forth between accounts, and was never notified of the new mail.

(?)

---

