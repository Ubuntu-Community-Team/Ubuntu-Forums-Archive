---
title: "COMMAND copy"
date: 2014-11-23
forum: General Help
---

### Post by den_ on 2014-11-23
Dear all,

I have noticed a process named 'copy', which seems to be active while, for example the 'aptitude update' command is running. Can anyone provide me with some info about this process, like what it is, what it does etc? It opens a pseudo terminal, and pipes, but doesn't explain much...: 

> -dskp:~$ sudo ls -la /proc/7773/fd
total 0
dr-x------ 2 root root  0 Nov 24 01:22 .
dr-xr-xr-x 9 root root  0 Nov 24 01:22 ..
lr-x------ 1 root root 64 Nov 24 01:22 0 -> pipe:[237407]
l-wx------ 1 root root 64 Nov 24 01:22 1 -> pipe:[237406]
lrwx------ 1 root root 64 Nov 24 01:22 2 -> /dev/pts/12

I am asking b/c I cannot find any executable file with that name. Actually there is a PostgreSQL COPY command, but that'S definitely not it.

---

### Post by nerdtron on 2014-11-24
What does "ps aux | grep -i copy" output when it is running?

---

### Post by den_ on 2014-11-24
> **nerdtron said:**
> What does "ps aux | grep -i copy" output when it is running?

Great, thank you for your reply! So ps aux shows the full path to the executable... Do you have it on your system(s) too?

> p:~$ ps aux | grep -i copy
root     15442  107  0.0  36388  4568 pts/12   R+   23:57   0:01 /usr/lib/apt/methods/copy

---

### Post by mJayk on 2014-11-25
Hay its on my system under the same path, cant help you with info regarding its purpose but I have it.

---

