---
title: "Tast manager?"
date: 2008-06-03
forum: General Help
---

### Post by cloroxmartini on 2008-06-03
So I'm installing this one program called tuxguitar and I see that the bar isn't moving much so I close the install window but the install manager is still there but I can't close it.  So I closed my account and logged back on and tried to install it again.  Now here's the problem...When I try to install it, it says that the install manager is already running.  Only thing is, I don't know how to close it so I can install anything else, not just tuxguitar.  Is there like a task manager I can open to close the install manager from before so I can go and install new programs?

---

### Post by tomcheng76 on 2008-06-03
perhaps
1. open up your console
2.> ps aux |grep tuxguitar
3. rember the PID(process ID) of the process
4. > kill -9 <PID of the process>

Example (i want to force terminate "vim" process):
> $ps aux |grep vim
root     17388  0.1  0.7  95888  2836 pts/1    S+   14:58   0:00 vim
root     17424  0.0  0.1  61152   672 pts/0    R+   14:59   0:00 grep vim

remember 17388 (it is not 17424, because "grep" is a search tool that you just used it!)

Finally, type
> kill -9 17388
to kill the "vim"
-9 means force terminate

---

### Post by markbusu on 2008-06-03
You can perform either of the following:

1. In Terminal type

```
sudo top
``` 

and kill the process if you see it listed.

2. Use the System Monitor System > Administration and kill the process

3. In Terminal Type

```
sudo ps aux
```

Get the PID of the process of the installation then enter

sudo kill -9 [Number of PID of the Process] and the process is killed.

Mark

---

### Post by cloroxmartini on 2008-06-03
I don't know if this changes anything but when I try and start Synaptic Package Manager, I get this error > E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried the two previous suggestions but I didn't get anywhere very quickly.

---

### Post by mali2297 on 2008-06-03
> **cloroxmartini said:**
> I don't know if this changes anything but when I try and start Synaptic Package Manager, I get this error 

I tried the two previous suggestions but I didn't get anywhere very quickly.

In a terminal, run
```

sudo pkill synaptic
sudo dpkg --configure -a

```
If you get any error messages, post them here. Otherwise, try now to open Synaptic.

---

### Post by cloroxmartini on 2008-06-03
Cool.  It worked beautifully.  Thanks guys.

---

