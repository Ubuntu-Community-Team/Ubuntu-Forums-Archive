---
title: "Problem with Nautilus?"
date: 2007-04-17
forum: General Help
---

### Post by efreddi on 2007-04-17
Hi All,

I have a problem with Ubuntu: at the start up of the desktop, after the login, I receive an error message through the Bug Buddy. The error comes from CD/DVD Creator. As result the full desktop is empty, no way to visualize the files on it. Then whenever I try to launcha  software from the main menu Places I get the same error.
I tried to submit the bug, but I received a main that there are no enough infotmation to process it.
Thanks for any suggestion!


Elia

PS: all the other programs work fine!

This is the detail reported by Bug Buddy:

[I]Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 38854656 vsize: 0 resident: 38854656 share: 0 rss: 11268096 rss_rlim: 0
CPU usage: start_time: 1176835089 rtime: 0 utime: 51 stime: 0 cutime:47 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226549584 (LWP 6807)]
(no debugging symbols found)
...
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb76da323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e711b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7403770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7404ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7670122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7670159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76701d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0x08100587 in nautilus_file_ref ()
#11 0x080f73f9 in nautilus_directory_ref ()
#12 0x0806c001 in POA_Nautilus_MetafileMonitor__init ()
#13 0x0806cb59 in POA_Nautilus_MetafileMonitor__init ()
#14 0xb770e89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#15 0xb76f5952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#16 0xb76f3bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#17 0xb76f473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb76f48f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#19 0x0806c243 in POA_Nautilus_MetafileMonitor__init ()
#20 0x080951bc in POA_Nautilus_MetafileMonitor__init ()
#21 0x0809521a in POA_Nautilus_MetafileMonitor__init ()
#22 0x0809d463 in POA_Nautilus_MetafileMonitor__init ()
#23 0xb770e6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#24 0xb76f5952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#25 0x0809d1b3 in POA_Nautilus_MetafileMonitor__init ()
#26 0xb76f3bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#27 0xb76f47e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#28 0xb7cc8038 in gtk_widget_new () from /usr/lib/libgtk-x11-2.0.so.0
#29 0x08069c58 in POA_Nautilus_MetafileMonitor__init ()
#30 0x08069d87 in POA_Nautilus_MetafileMonitor__init ()
#31 0x0808f5fa in POA_Nautilus_MetafileMonitor__init ()
#32 0xb774dcd0 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
#33 0x08067900 in ?? ()
#34 0x081cd100 in ?? ()
#35 0x08164be4 in ?? ()
#36 0x00000001 in ?? ()
#37 0x00000000 in ?? ()

Thread 1 (Thread -1226549584 (LWP 6807)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76da323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e711b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7403770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7404ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7670122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7670159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76701d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0x08100587 in nautilus_file_ref ()
No symbol table info available.
#11 0x080f73f9 in nautilus_directory_ref ()
No symbol table info available.
#12 0x0806c001 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#13 0x0806cb59 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#14 0xb770e89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb76f5952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb76f3bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb76f473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb76f48f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0x0806c243 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#20 0x080951bc in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#21 0x0809521a in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#22 0x0809d463 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#23 0xb770e6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb76f5952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0x0809d1b3 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#26 0xb76f3bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb76f47e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb7cc8038 in gtk_widget_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0x08069c58 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#30 0x08069d87 in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#31 0x0808f5fa in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#32 0xb774dcd0 in ORBit_c_stub_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#33 0x08067900 in ?? ()
No symbol table info available.
#34 0x081cd100 in ?? ()
No symbol table info available.
#35 0x08164be4 in ?? ()
No symbol table info available.
#36 0x00000001 in ?? ()
No symbol table info available.
#37 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()[/I]

---

