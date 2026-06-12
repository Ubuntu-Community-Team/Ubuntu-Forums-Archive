---
title: "WINE Error - X11DRV_CritSection&quot; wait timed out"
date: 2007-01-11
forum: General Help
---

### Post by vibranze on 2007-01-11
guys,

i've encountered wine problem with the following error, previously was running perfectly. i believe it is caused by the system upgrade. i'm using ubuntu edgy on nec versa s940 laptop, vga driver is i810 with 1280x768 resolution.

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
err:ntdll:RtlpWaitForCriticalSection section 0x7eb6a360 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
xxx@tn888:~$ wine: Critical section 7eb6a360 wait failed at address 0x7bc2df40 (thread 000c), starting debugger...
Unhandled exception: wait failed on critical section 0x7eb6a360 thread_data_tls_index+0x44
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc2df40
Process of pid=0x0000000a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)

has anybody encountered the above error? i tried to downgrade wine up to version 0.9.24 but didn't help.

please help.

regards,
vibranze

---

### Post by vibranze on 2007-01-15
Hmm, seem that there is nobody can help me on my problem.

---

