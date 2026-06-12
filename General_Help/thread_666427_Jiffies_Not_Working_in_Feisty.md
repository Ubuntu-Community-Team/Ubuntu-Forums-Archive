---
title: "Jiffies Not Working in Feisty"
date: 2008-01-13
forum: General Help
---

### Post by GaryH on 2008-01-13
Hi Everybody,

jiffies.h isn't in the normal include path and the gcc linker can't find jiffies or get_jiffies_64(). Maybe there is a library which needs to be included or installed. Has anybody out there used jiffies? Any help will be much appreciated.

Peace,
GaryH

---

### Post by GaryH on 2008-01-14
Hi Everybody,

I was planning on using jiffies to measure time the difference between real time events to a resolution of .1 second. According to my research jiffies increment every 10 mSec and would work for my application. I found another way to measure time difference using the clock_gettime() C function. The function stuffs a timespec structure with the seconds and nano-seconds since bootup. The function prototype and structure definition is in time.h and gcc needs the -lrt switch to include the real time library.

On my old IBM T20 clock_gettime(CLOCK_REALIME, &ts), best case, resolves time differences to about 10 uSec. 

I'm still interested in finding out how to access the jiffy count should any jiffies guru run across this at a later date.

Peace,
Gary

---

