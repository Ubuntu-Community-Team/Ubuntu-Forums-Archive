---
title: "quick questions- processes"
date: 2006-08-14
forum: General Help
---

### Post by njzillest on 2006-08-14
whats the command to view all my background processes? I dont want a GUI application- i perfer CUI.

Right now im using GUI "System Monitor"

Thanks

---

### Post by 23meg on 2006-08-14
```
top
``````
ps
```

---

### Post by nanotube on 2006-08-14
the command is "ps"
to see all the processes, run "ps ax"
you can of course "man ps" for more commandline options.

there is also "top" which shows you some of the most active processes, as well as system utilization statistics.

---

### Post by njzillest on 2006-08-14
How do i Kill a process? I know how to use xkill.. But i wanna be able to do it through the COmmand line

thanks for the help :-D

---

### Post by 23meg on 2006-08-14
*killall *will let you stop a process by name. *kill *will let you stop them by PID (process ID).

---

