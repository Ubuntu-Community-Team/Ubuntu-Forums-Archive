---
title: "[SOLVED] mozilla wont close"
date: 2008-01-17
forum: General Help
---

### Post by LostLake on 2008-01-17
Sometimes Mozilla will crash and I have to force quit the program. Whenever it crashes and I try to restart, I am told that Mozilla is already running and I need to close it. The only solution I have come up with is to restart the computer. Any advice on another solution that doesn't involve restarting the computer?
Thanks.

---

### Post by pytheas22 on 2008-01-17
in a terminal, type

```
ps -e | grep firefox
```

it will give you the process ID of all processes using firefox (there will probably be two, I think)

to kill the process, type "kill" and the process numbers..e.g.

```
kill 4087 4175
```

or whatever the numbers are (they will be different all the time).

if that doesn't do it, ```
kill -9
``` is a more potent way of ending processes that are really misbehaving

---

### Post by pytheas22 on 2008-01-17
p.s., by "Mozilla" I was assuming you meant Firefox.  If not you will have to search for a different process name...or "mozilla" itself would probably work but I always just kill Firefox.

---

### Post by FenderGuy2112 on 2008-01-17
^ correct.....


You should start up firefox in the terminal so you can do more with it in case it freezes, it should be easier to kill it with the above line and have that full access with the terminal itself...

FenderGuy2112

---

### Post by bodhi.zazen on 2008-01-17
Or, for the lazy

kill -9 `pidof mozilla-firefox`

pidof is a commnd that returns the PID of a running process

Bu surrounding it in back tics ` (not single quotes ' ) we feed it directly to kill w/o having to do anything further.

---

### Post by LostLake on 2008-01-18
Thanks everybody. I'll try it next time firefox crashes.

---

### Post by Casual Fan on 2008-01-18
To avoid the command line altogether, click on System>Administration>System Monitor, click on the processes tab, look for Mozilla (or Firefox or whatever) and click on "End Process."

---

