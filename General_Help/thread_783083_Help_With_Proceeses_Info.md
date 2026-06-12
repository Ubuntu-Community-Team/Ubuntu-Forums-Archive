---
title: "Help With Proceeses Info"
date: 2008-05-05
forum: General Help
---

### Post by Mz7 on 2008-05-05
Hey guys how does Ubuntu manage processes?I checked in system monitor,bit similar to task manger from basic look.but what are the main differences when compared with Windows process management??

---

### Post by fahadsadah on 2008-05-05
In a terminal, type the following:
```
ps aux
```
That will list all running processes.
You can send [signals]("http://www.comptechdoc.org/os/linux/programming/linux_pgsignals.html") to any of these processes (for example, `kill -9 1234` where 1234 is the pid (the first number of the relevant line in the `ps aux` output))
There is an alternative called pkill that takes the command used to start the process as a parameter, rather than PID.
And despite the names, the two commands are used for things other than killing processes - there are many useful signals.

---

### Post by retrow on 2008-05-05
In System monitor, there is a column that shows 'Nice Level' which sets the priority of a running process. If you have multiple processes and you want some of them to have higher priority, you set their nice level to a lower value so that they get a higher preference while sharing the system resources.

---

### Post by fahadsadah on 2008-05-06
Yes. This number represents this processes **nice**ness to other processes in terms of system resources
You can start a process with a specific nice value using the nice command, with the following example: ```
nice processname number
```

---

