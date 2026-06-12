---
title: "Login problems"
date: 2007-04-16
forum: General Help
---

### Post by Jesuses Left Leg on 2007-04-16
Ok, I am running Ubuntu 6.10 and am not new to linux but new to gnome. I used to have Kubuntu but recently switched. The problem is i logged out and tried to log in again but it brings up the background for the splash image but does not load any of the list of things it usually does (best way I can describe it).
Then I try log in in failsafe mode which works but i get this error when i have logged in.
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

EDIT: Also I ran 'gnome-settings-daemon' and got this
[spoiler]> Memory status: size: 28467200 vsize: 0 resident: 28467200 share: 0 rss: 7294976 rss_rlim: 0
CPU usage: start_time: 1176745977 rtime: 0 utime: 10 stime: 0 cutime:8 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-settings-daemon'

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
[Thread debugging using libthread_db enabled]
[New Thread -1225849168 (LWP 6215)]
[New Thread -1227359328 (LWP 6217)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb787934b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f761b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0806915d in keyboard_config_registry_get_type ()
#5  0xb78a989a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#6  0xb7890952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#7  0xb788ebdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#8  0xb788f73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#9  0xb788f8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
#11 0x080551ea in gnome_settings_daemon_new ()
#12 0x08053efc in main ()

Thread 2 (Thread -1227359328 (LWP 6217)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb78783fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb77e045d in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb77fd38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7872504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb773051e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1225849168 (LWP 6215)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb787934b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f761b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0806915d in keyboard_config_registry_get_type ()
No symbol table info available.
#5  0xb78a989a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb7890952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb788ebdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb788f73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb788f8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
No symbol table info available.
#11 0x080551ea in gnome_settings_daemon_new ()
No symbol table info available.
#12 0x08053efc in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
[/spoiler]

Can anybody tell me what the problem is.
Thanks.

---

