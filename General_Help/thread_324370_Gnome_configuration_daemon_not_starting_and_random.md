---
title: "Gnome configuration daemon not starting and random crashes at session startup"
date: 2006-12-23
forum: General Help
---

### Post by finferflu on 2006-12-23
Hi all,

I think I'm messing up my system. So far I've installed Ubuntu, then Kubuntu and removed Ubuntu, then installed fluxbox, then IceWM, and now I've just reinstalled Ubuntu. 

The results are as follows:

1. I no longer have a graphical login (I had opted for gdm during the installation, but it doesn't start up automatically.

2. As soon as my Gnome session starts, I got the following errors:

A bug report for a random application (I think it's random, since everytime I start Gnome the backtrace comes from a different app), this time I've got this backtrace:

Memory status: size: 37658624 vsize: 0 resident: 37658624 share: 0 rss: 10797056 rss_rlim: 0
CPU usage: start_time: 1166908990 rtime: 0 utime: 113 stime: 0 cutime:109 cstime: 0 timeout: 4 it_real_value: 0 frequency: 10

Backtrace was generated from '/usr/libexec/evolution-exchange'

```
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1234352464 (LWP 4916)]
[New Thread -1235936352 (LWP 4953)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb6f0d34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7c8c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb650da70 in ?? ()
#5  0xb774d021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
#6  0xb774e78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb77503bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb77507bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb6e99802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb6e9c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb6e9cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb716fa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#13 0x0805b9b3 in main ()

Thread 2 (Thread -1235936352 (LWP 4953)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6df4803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb6e9c813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb6e9cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb6fbb7e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb6eb738f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb6f06504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb6dfe51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1234352464 (LWP 4916)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6f0d34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7c8c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb650da70 in ?? ()
No symbol table info available.
#5  0xb774d021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#6  0xb774e78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0xb77503bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0xb77507bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#9  0xb6e99802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb6e9c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb6e9cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb716fa23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#13 0x0805b9b3 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

And then I get a message saying that Gnome Configuration Daemon couldn't be started.

I have deleted my .gnome directory in my home folder, but it doesn't seem to make any difference...

Any hint please?

Thanks for your time :)

---

### Post by hanzomon4 on 2006-12-23
Try this ```
sudo aptitude reinstall gdm gnome-session
```

---

### Post by finferflu on 2006-12-24
> **hanzomon4 said:**
> Try this ```
sudo aptitude reinstall gdm gnome-session
```

Thanks for your reply, but it didn't work, everything is just as above...

---

### Post by finferflu on 2006-12-25
Anyone there who can help me please? I really would like my Gnome back!

---

### Post by debiannerd on 2007-01-01
> **finferflu said:**
> Anyone there who can help me please? I really would like my Gnome back!

reinstall :mrgreen: 

Try this

Go in console mode "Alt-F2"
> 
apt-get --purge remove gnome* gdm*
apt-get autoclean
apt-get update
apt-get -u upgrade
apt-get install gnome gdm
apt-get autoclean


---

