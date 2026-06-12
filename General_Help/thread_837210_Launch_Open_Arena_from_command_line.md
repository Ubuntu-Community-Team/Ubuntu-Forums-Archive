---
title: "Launch Open Arena from command line"
date: 2008-06-22
forum: General Help
---

### Post by High_Yield on 2008-06-22
Hi...

For performance reasons I want to run Open Arena from the command line - without GDM at all.

Details:
1) With GDM running, Open Arena runs fine using the NVidida drivers - no problems at all.
2) I have disabled GDM during boot using rcconf at it works just fine.  Boots to a command line.
3) I can change directories and "launch" open arena using something like ./ioquake3-smp.i386.  Anyway, it does try to run but fails loading the gl subsystem, like: Sys_Error: GLimp_Init() - could not load OpenGL subsystem

So, how can I get OA to run from the command line without using GDM - or is GDM mandatory?

Thanks a million - B

---

### Post by fahadsadah on 2008-06-22
Sorry, you need GDM.

---

### Post by High_Yield on 2008-06-22
Ouch - can anyone else validate that - or give a reason why ?

Thanks - B

---

