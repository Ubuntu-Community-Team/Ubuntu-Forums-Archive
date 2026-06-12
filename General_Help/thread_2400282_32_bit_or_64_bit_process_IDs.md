---
title: "32 bit or 64 bit process IDs"
date: 2018-09-04
forum: General Help
---

### Post by Skaperen on 2018-09-04
i see a lot of code and headers in the kernel to support 32 bit and even 64 bit process IDs and other things such as user ID numbers.  so, what more does it take to actually use these?  is setting the maximum process ID enough or is there more code to be changed?  is there more kernel changes needed? is there more userland changes needed, like being able to handle numbers larger than 16 bits?  can i at least go up to 65535?

---

### Post by dsstorefile1 on 2018-09-06
You can temporarily increase the PID cap up to 4194304 for 64-bit systems by writing an integer to /proc/sys/kernel/pid_max. A permanent configuration involves [FONT=lucida console]sysctl[/FONT].

---

### Post by Skaperen on 2018-09-07
so the current limit is for 32-bit PIDs.  is that because it gets handled in syscalls via signed ints?  what about a 63-bit int?  or is not all of the kernel and appropriate userland code ready to go beyond 32 bits for PIDs?

---

