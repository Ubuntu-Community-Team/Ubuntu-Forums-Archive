---
title: "Trying to work with bluefish but can't save"
date: 2006-12-06
forum: General Help
---

### Post by Jammy_Stuff on 2006-12-06
I've finally decided to stop using my last Windows program (I was using my Windows web development app through Wine but the fonts were annoying me) and installed Bluefish using synaptic. I opened it and thought I'd better just do a simple HTML file to make sure everything works. However, when I tried to save it, I got a pop up letting me know the program has crashed and giving me this report:

> 
Memory status: size: 74752000 vsize: 0 resident: 74752000 share: 0 rss: 16588800 rss_rlim: 0
CPU usage: start_time: 1165442952 rtime: 0 utime: 121 stime: 0 cutime:113 cstime: 0 timeout: 8 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/bluefish'

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
[Thread debugging using libthread_db enabled]
[New Thread -1226463568 (LWP 17985)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb741434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb77f41b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x08071e27 in ?? ()
#5  0x084d0800 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1226463568 (LWP 17985)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb741434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb77f41b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x08071e27 in ?? ()
No symbol table info available.
#5  0x084d0800 in ?? ()
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


I can't seem to get it to save at all. I'm running Edgy with the 2.6.17-10-generic kernel. Any ideas?

---

### Post by TattooedFish on 2006-12-06
Bluefish runs fine for me, never had any problem.

Maybe uninstall/remove it and then install/add it again?

Any other program that's doing the same, or it's just Bluefish?

---

