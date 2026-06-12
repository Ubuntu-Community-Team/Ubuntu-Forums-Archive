---
title: "Jiffies.h Include Path"
date: 2008-01-13
forum: General Help
---

### Post by GaryH on 2008-01-13
Hi Everybody,
I'm having trouble including jiffies.h in a C program. > jiffie_test.c:2:27: error: linux/jiffies.h: No such file or directoryI thought including it would be as simple as > #include <linux/jiffies.h>?or > #include <jiffies.h>? I noticed jiffies.h and associated .h files are missing from /usr/include but are included with the kernel headers. Adding an include directory to gcc is no big deal but seems inappropriate to do for a kernel header.  Is this the way it is supposed to be or is my  system hosed up or do I just not know what the heck I'm doing?
Peace,
GaryH

---

### Post by GaryH on 2008-01-13
Everybody,
I didn't include jiffies.h in the C program and used extern instead. The program compiled just fine but failed to link either jiffies or get_jiffies_64().  I wonder if 7.04 supports jiffies. Maybe there is a library which needs to be included or installed. I'm going to open another thread and ask. I searched Ubuntu for jiffies and found 0 matches.:confused:
Peace,
GaryH

---

