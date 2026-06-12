---
title: "errors on install and warning that it may not restart"
date: 2006-10-27
forum: General Help
---

### Post by chris.olsen on 2006-10-27
That is what I got after install, one error created a log file for it (shown below) and the worst was after it was all done it said that it might not restart.  It said to run gksu "update manager -c", which I did, although nothing really seemed to happen in that nothing was displayed in the terminal.

It did start up ok, but is there anything that I should check to make sure all is well?  

Thanks

================================================
Don't know how useful this is...
================================================
Memory status: size: 21741568 vsize: 0 resident: 21741568 share: 0 rss: 12636160 rss_rlim: 0
CPU usage: start_time: 1161950896 rtime: 0 utime: 457 stime: 0 cutime:253 cstime: 0 timeout: 204 it_real_value: 0 frequency: 322

Backtrace was generated from '/usr/bin/update-notifier'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb751f463 in ?? ()
#2  0xb7fcef58 in ?? ()
#3  0xb7f9c8e6 in ?? ()
#4  0x00000a30 in ?? ()
#5  0xbfcf91c8 in ?? ()
#6  0x00000000 in ?? ()

---

