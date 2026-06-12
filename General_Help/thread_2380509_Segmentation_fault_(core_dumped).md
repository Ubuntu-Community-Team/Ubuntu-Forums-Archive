---
title: "Segmentation fault (core dumped)"
date: 2017-12-18
forum: General Help
---

### Post by future.progrr on 2017-12-18
Hello,

I am having an intel integrated gpu and an nvidia dedicated gpu. I installed the nvidia driver today, enabled it and afterwards unity-control-center wouldn't work anymore.
I am running Ubuntu, this is the error that I get:

get chip id failed: -1 [13]
param: 4, val: 0
[intel_init_bufmgr:1193] Error initializing buffer manager.


(unity-control-center:18953): GLib-CRITICAL **: g_strsplit: assertion 'string != NULL' failed
Segmentation fault (core dumped)

Please help me, I really want to use my dedicated gpu. Thanks a lot

---

### Post by #&amp;thj^% on 2017-12-18
> **future.progrr said:**
> Hello,

I am having an intel integrated gpu and an nvidia dedicated gpu. I installed the nvidia driver today, enabled it and afterwards unity-control-center wouldn't work anymore.
I am running Ubuntu, this is the error that I get:

get chip id failed: -1 [13]
param: 4, val: 0
[intel_init_bufmgr:1193] Error initializing buffer manager.


(unity-control-center:18953): GLib-CRITICAL **: g_strsplit: assertion 'string != NULL' failed
Segmentation fault (core dumped)

Please help me, I really want to use my dedicated gpu. Thanks a lot
Try this command:
```
setsid unity
```
and then restarting.

---

### Post by future.progrr on 2017-12-19
> **1fallen said:**
> Try this command:
```
setsid unity
```
and then restarting.

Thanks a lot, it definetly works. Can you please explain to me what this did tho? And why was the problem there in the first place?

---

### Post by #&amp;thj^% on 2017-12-19
Just reorders some parts that did not load right.
```
NAME
       setsid - run a program in a new session

SYNOPSIS
       setsid [options] program [arguments]

DESCRIPTION
       setsid  runs  a  program in a new session. The command calls fork(2) if
       already a process group leader. Otherwise, it executes a program in the
       current process.



```

If you find the need to keep doing this with every reboot, then open a terminal, then,

```
sudo nano /etc/rc.local
```

then add

```
setsid unity

```
before

```
exit 0
```

save and you are done. If satisfied with this will you be as kind to mark this as solved to help others.:)
Kind Regards

---

### Post by ddascalescu+launchpad on 2017-12-27
On Ubuntu 16.04.3, running "[COLOR=#000000][FONT=&quot]setsid unity[/FONT][/COLOR]" led to a complete mess:

1. Unity disappeared. No task bar, no window chrome, Alt+Tab didn't work.
2. After rebooting a bunch of times, I ended up in a login loop. Had to login in the console (Ctrl+Alt+F1) and run "mv .XAuthority .XAuthority.bak"

This is really lame. I paid money for a laptop with a dedicated graphics card and I can't use it.

---

