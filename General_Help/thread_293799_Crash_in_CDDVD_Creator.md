---
title: "Crash in CD/DVD Creator"
date: 2006-11-05
forum: General Help
---

### Post by hbchrist on 2006-11-05
This is a wierd one. I have been using 6.10 without issue for quite a while. Tonight, while copying files from my workstation to a remote share on a Mac workstation, I unmounted (or tried to, that is) a separate share located on the same Mac workstation.

Suddenly, I get the bug buddy. I will post the bug below, but the short story is that I can no longer browse the network, mount remote shares of any type, or even open my home folder from the Places-->Home Folder drop down menu.

When I try to do any of those things, I get the bug buddy, and I have a split second to see the culprit listed as CD/DVD Creator. Gnome itself still launches. I can run all my applications including Firefox, Thunderbird, Mplayer, you name it. I can also run all the utilities and admin tools. I just can't open folders. 

Very wierd. I tried running apt-get -f install to "fix" any broken packages, but everything came up a-OK. Bugzilla tells me that it is aware of this bug, but no progress has been made on it. A search of the forums comes up empty, so it's possible I may not be looking for the correct error. Anyway, here is the bug report. Any ideas on how to fix this would be greatly appreciated.

TIA.

Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 39591936 vsize: 0 resident: 39591936 share: 0 rss: 11464704 rss_rlim: 0
CPU usage: start_time: 1162770512 rtime: 0 utime: 30 stime: 0 cutime:30 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/nautilus'

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
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226664272 (LWP 5332)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb76bb323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e521b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb73e4770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb73e5ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7651122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7651159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76511d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0x08100547 in nautilus_file_ref ()
#11 0x080f73b9 in nautilus_directory_ref ()
#12 0x0806c001 in POA_Nautilus_MetafileMonitor__init ()
#13 0x0806cb59 in POA_Nautilus_MetafileMonitor__init ()
#14 0xb76ef89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#15 0xb76d6952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#16 0xb76d4bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#17 0xb76d573f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb76d58f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#19 0x0806c243 in POA_Nautilus_MetafileMonitor__init ()
#20 0x080951bc in POA_Nautilus_MetafileMonitor__init ()
#21 0x0809521a in POA_Nautilus_MetafileMonitor__init ()
#22 0x0809d463 in POA_Nautilus_MetafileMonitor__init ()
#23 0xb76ef6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#24 0xb76d6952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#25 0x0809d1b3 in POA_Nautilus_MetafileMonitor__init ()
#26 0xb76d4bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#27 0xb76d57e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#28 0xb7ca9038 in gtk_widget_new () from /usr/lib/libgtk-x11-2.0.so.0
#29 0x08069c58 in POA_Nautilus_MetafileMonitor__init ()
#30 0x08069d87 in POA_Nautilus_MetafileMonitor__init ()
#31 0x0808f5fa in POA_Nautilus_MetafileMonitor__init ()
#32 0xb772ecd0 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
#33 0x08067900 in ?? ()
#34 0x081cf830 in ?? ()
#35 0x08164ba4 in ?? ()
#36 0x00000001 in ?? ()
#37 0x00000000 in ?? ()

Thread 1 (Thread -1226664272 (LWP 5332)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76bb323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e521b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb73e4770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb73e5ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7651122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7651159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76511d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0x08100547 in nautilus_file_ref ()
No symbol table info available.
#11 0x080f73b9 in nautilus_directory_ref ()
No symbol table info available.
#12 0x0806c001 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#13 0x0806cb59 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#14 0xb76ef89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb76d6952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb76d4bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb76d573f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb76d58f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0x0806c243 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#20 0x080951bc in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#21 0x0809521a in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#22 0x0809d463 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#23 0xb76ef6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb76d6952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0x0809d1b3 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#26 0xb76d4bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb76d57e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb7ca9038 in gtk_widget_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0x08069c58 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#30 0x08069d87 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#31 0x0808f5fa in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#32 0xb772ecd0 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#33 0x08067900 in ?? ()
No symbol table info available.
#34 0x081cf830 in ?? ()
No symbol table info available.
#35 0x08164ba4 in ?? ()
No symbol table info available.
#36 0x00000001 in ?? ()
No symbol table info available.
#37 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by Mahmoud on 2006-11-30
There are lots (2580+) bugs submitted to Gnome (most through BugBuddy) from users about the "Crash in CD/DVD Creator":
[http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=crash+Creator](http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=crash+Creator)

Many from Ubuntu users (300+). 
[http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=crash+Creator&long_desc_type=substring&long_desc=Distribution%3A+Ubuntu&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=](http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=crash+Creator&long_desc_type=substring&long_desc=Distribution%3A+Ubuntu&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=)

Nautilus crashes (sometimes CD/DVD creator too) when opening the properties of any ODP (Open Office Presentation) here.

---

