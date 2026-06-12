---
title: "Shutting down a program that runs when the window isnt open"
date: 2008-07-03
forum: General Help
---

### Post by DarK420 on 2008-07-03
How do i do this ?
Like say i close utorrent but its still running..
In windows theres a task manager is there something similar to it in linux?

Thanks

---

### Post by dje on 2008-07-03
System >> Administration >> System Monitor and click on the 'Processes' tab

hope that helps,
dje

---

### Post by iaculallad on 2008-07-03
Or, if you want to display running processes in the terminal, use:

```
top
```

OR

```
htop
```

but you need to install it first (sudo apt-get install htop)

---

### Post by diafanos on 2008-07-03
a really useful command I use is 
```
killall <program_name>
```

for example when even though I have close firefox, and I try to reopen it, says that it is still running, I just type
```
killall firefox
```

Also using ***_top_*** command you can do the following:

run from terminal **top** command. A list of running processes is appeared. Find the one you want to stop and press ***k***. then type the PID number of this process to kill it!

---

### Post by sujoy on 2008-07-03
ps ax | grep program_name

see the process id
kill process_id
or 
kill -9 process_id

---

### Post by monoufo on 2008-07-06
haha, this is linux.  You just got half a dozen different ways to do it.

---

