---
title: "memory usage for specific program"
date: 2008-01-13
forum: General Help
---

### Post by monkeyking on 2008-01-13
Hi,
is there some way to check memory usage of a specific program?

top shows all,
and I just want one program.

thanks in advance

---

### Post by SOULRiDER on 2008-01-13
```
ps aux
``` will display stats for all programs. You can pipe that to grep and filter out unwanted lines. So say you want to see the mem usage for the program xchat for example, you can do
```
ps aux | grep xchat
```
The different columns mean different things.
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```
That means you want the third column.

In my case the output og ps aux | grep xchat is:
> mauro    12958  0.3  1.7  35448 17828 ?        S    03:33   0:16 xchat meaning xchat is using 1.7% of my memory.

I hope that was useful :)

---

### Post by ghostdog74 on 2008-01-13
top doesn't just shows all. Look at the man page. It can do other stuff like showing process by pid etc... anyway. to use top to display vmware process for example
```

# top -n 1 | awk '/vmware/{print $10}' 

```

---

