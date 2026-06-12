---
title: "restart a process with terminal"
date: 2008-01-08
forum: General Help
---

### Post by fizzle101 on 2008-01-08
hi

please i want to know if there is a way to restart a running process from terminal.

for example. say i am already running firefox. is there a terminal command that can close it and reopen it again.

any help is welcomed please.

---

### Post by dcstar on 2008-01-08
> **fizzle101 said:**
> hi

please i want to know if there is a way to restart a running process from terminal.

for example. say i am already running firefox. is there a terminal command that can close it and reopen it again.

any help is welcomed please.

You can find the process ID and use that to kill or restart it:

```
ps -ef | grep firefox
man kill
```

---

### Post by PinkFloyd102489 on 2008-01-08
Hit alt+F2 and enter this:


```
killall firefox-bin && firefox
```



Obviously replace firefox with whatever you wanting.

---

### Post by fizzle101 on 2008-01-08
> **PinkFloyd102489 said:**
> Hit alt+F2 and enter this:


```
killall firefox-bin && firefox
```



Obviously replace firefox with whatever you wanting.


Thank you. that helped

---

