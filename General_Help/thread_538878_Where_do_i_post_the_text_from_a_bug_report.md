---
title: "Where do i post the text from a bug report?"
date: 2007-08-30
forum: General Help
---

### Post by spotdog14 on 2007-08-30
For some reason i keep getting a bug report that cannot be sent to gnome because it is not recognized. Where do i post it, or get help with making it stop showing up?

Here is the text:

System: Linux 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
X Vendor: The X.Org Foundation
X Vendor Release: 70200000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Glossy
Icon Theme: gnome

Memory status: size: 1757184 vsize: 1757184 resident: 491520 share: 421888 rss: 491520 rss_rlim: 4294967295
CPU usage: start_time: 1188498092 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/libexec/evolution-data-server-1.10'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ec974e in wait4 () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ec9727 in wait3 () from /lib/tls/i686/cmov/libc.so.6
#3  0x0804f274 in ?? ()
#4  0xbf8d4a20 in ?? ()
#5  0x00000000 in ?? ()
The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]


----------- .xsession-errors ---------------------
alarm-queue.c:560 (load_alarms_for_today) - From Thu Aug 30 14:21:09 2007
 to Thu Aug 30 14:21:09 2007
alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80dbb10: Received at thread b3649b90
alarm-queue.c:2008 (alarm_queue_add_async) - 0x80d26b0
alarm-notify.c:337 (alarm_msgport_replied) - 0x80d5c50: Replied to GUI thread
alarm-queue.c:560 (load_alarms_for_today) - From Thu Aug 30 14:21:09 2007
 to Thu Aug 30 14:21:09 2007
alarm-queue.c:497 (load_alarms) 
alarm-queue.c:526 (load_alarms) - Setting Call backs 
alarm-notify.c** Message: <information>	You are now connected to the wireless network 'MSUNet Wireless'.
--------------------------------------------------

---

### Post by yabbadabbadont on 2007-08-30
Search for an existing bug report for this issue at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

If you can't find any that seem to match your issue, create a new one.

---

