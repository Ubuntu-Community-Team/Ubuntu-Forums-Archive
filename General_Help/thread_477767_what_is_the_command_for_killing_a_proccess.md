---
title: "what is the command for killing a proccess?"
date: 2007-06-18
forum: General Help
---

### Post by swoll1980 on 2007-06-18
Let me know please

---

### Post by 5-HT on 2007-06-18
killall <process name>

Or

kill <optional signal> <PID>

Or

xkill  (for a point and click way to end a process)

Please refer to the respective manual pages for each command for more details.

---

### Post by H.E. Pennypacker on 2007-06-18
Or press ALT-F2, type xkill, and click on the window you'd like to kill with the skull.

---

### Post by swoll1980 on 2007-06-18
thanks guys

---

### Post by stchman on 2007-06-18
> **swoll1980 said:**
> Let me know please

you can do a ps-ef at a terminal and then find the offending process.  You can then type kill <process number> and that will kill the process.

Alternatively is you install the system monitor it has a processes tab in which you can kill processes.

---

