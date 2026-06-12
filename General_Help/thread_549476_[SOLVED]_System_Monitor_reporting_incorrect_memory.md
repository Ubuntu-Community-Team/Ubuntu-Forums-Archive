---
title: "[SOLVED] System Monitor reporting incorrect memory usage"
date: 2007-09-12
forum: General Help
---

### Post by AbredPeytr on 2007-09-12
I have a weird problem. I've used system monitor to check out what is running on my computer and how much memory is being used for each program. I have a laptop with a 60GB harddrive. In system monitor under the memory column, programs that I've started all are using 17179869180.1 GB

What's up with that?

---

### Post by DrumScum on 2007-10-28
I have the same issue, but not with all processes. See screenshot.

---

### Post by Snoober on 2007-11-30
I found out that it's something to do with XGL. By uninstalling/disabling it the memory went back to normal. Anybody know how to fix this because i'm having the same issue.

---

### Post by AbredPeytr on 2007-12-01
> **Snoober said:**
> I found out that it's something to do with XGL. By uninstalling/disabling it the memory went back to normal. Anybody know how to fix this because i'm having the same issue.

Thanks for the info. I maybe I'll get motivated this weekend and file a bug report with this information.

---

### Post by -grubby on 2007-12-01
oh well, you can always type ```
top
``` in a terminal to do it

---

### Post by AbredPeytr on 2007-12-02
> **nathangrubb said:**
> oh well, you can always type ```
top
``` in a terminal to do it

Thanks!  That's even better.

---

### Post by ronocdh on 2008-02-28
Uh... I don't see why this thread is marked as "solved" just because someone proposed using "top" instead of the sysmonitor. Has anyone made progress on this? It's driving me nuts.

I believe it has to do with 64-bit and xgl together.

---

