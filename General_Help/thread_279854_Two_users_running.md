---
title: "Two users running?"
date: 2006-10-18
forum: General Help
---

### Post by Jordan Meeter on 2006-10-18
Hey,

I just did

> jordan@jordan-desktop:~$ uptime
 15:59:50 up 58 min,  2 users,  load average: 0.63, 0.59, 0.46

Are those load averages good or bad? And why are there two users running?

Thanks

---

### Post by njohn858 on 2006-10-18
I am not sure about the load averages, but it IS normal to have two users logged on. If you run

who

it will show you who is logged on. Typically you will see your user name listed twice. If you switch to another TTY session (CTRL+ALT+F#) and log in there and type 'who' you will see three users logged on. (Your desktop normally runs on TTY7 so to get back to it hit CTRL+ALT+F7)

---

### Post by Jordan Meeter on 2006-10-18
What is TTY? And what is the purpose of having two users running though? Would that by any chance affect my computer's performance?

---

### Post by IYY on 2006-10-18
To be logged in really just means to be running a shell. For example, if you open a hundred terminals you will see 100 users logged in (all you). This does not really affect your performance, since a "log in" does not actually mean running any programs other than the shell.

---

