---
title: "Resource temporarily unavailable"
date: 2022-04-21
forum: General Help
---

### Post by NotQuiteSU on 2022-04-21
I have a script which accesses resources on a mounted share from a NAS.  (scripts, lists files)

  Last night, my script errored

  <mount path>: Resource temporarily unavailable
  It's happened in the past and a reboot fixes it for some time. But wanted to identify and fix the underlying cause.

---

### Post by Doug S on 2022-04-21
The "Resource temporarily unavailable" error is typically due to reaching the limit for the number of processes. Does your script spawn a lot of threads? The limits can be increased. Until I have time to copy it to here, see an answer I did over on [askubuntu.com]("https://askubuntu.com/questions/845380/bash-fork-retry-resource-temporarily-unavailable/883677#883677")

---

### Post by NotQuiteSU on 2022-04-21
It could. But the script runs without issue countless times. Weeks/months at a time. Is there a way to track how many processes are in use?

---

### Post by ActionParsnip on 2022-04-21
Does the mount drop off? Have an extra part of the script that uses 'touch' to put a file on the share before running the rest. If that fails then send an email or an alert of some kind.
May help

---

### Post by Doug S on 2022-04-21
Something like this:
```
doug@s19:~/s19-diag$ cat proc-count-mon
#!/bin/dash

echo "User Processes Count Monitor"
cat /sys/fs/cgroup/pids/user.slice/pids.current > upcm-data
sleep 5.0
while [ 1 ];
do
  cat /sys/fs/cgroup/pids/user.slice/pids.current >> upcm-data
  sleep 5.0
done
```Where you would select the sleep time based on your requirements.

Example:

```
doug@s19:~/s19-diag$ cat upcm-data
10
10
10
15682  [COLOR="#FF0000"]<<< I am spinning out 60,000 threads[/COLOR]
43177
60011  [COLOR="#FF0000"]<<< Finished spawning the threads[/COLOR]
60011
...
60011
60011
60016  [COLOR="#FF0000"]I am logging in to another SSH session to check on things[/COLOR]
60014
60014
...
60014
59316  [COLOR="#FF0000"]Killed the high thread count program.[/COLOR]
13
13
13
13
```

---

### Post by NotQuiteSU on 2022-04-21
top - 10:33:08 up 8 days, 22:43,  2 users,  load average: 0.16, 0.17, 0.15
Tasks: 201 total,   1 running, 200 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.9 us,  0.3 sy,  0.0 ni, 98.7 id,  0.0 wa,  0.0 hi,  0.1 si,  0.0 st
MiB Mem :   7838.3 total,    125.1 free,   1922.2 used,   5791.0 buff/cache
MiB Swap:   8117.0 total,   7279.0 free,    838.0 used.   5609.6 avail Mem

> cat /sys/fs/cgroup/pids/user.slice/user-1000.slice/pids.current
16

> $ cat /proc/sys/kernel/pid_max
4194304

> $ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 30996
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 30996
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

---

### Post by Doug S on 2022-04-21
Was your post data aquired while your script was running? What I do not know is if there are other reasons for the "Resource temporarily unavailable" error, such as what ActionParsnip was suggesting. I would definitely raise your files limit (I do not understand why the default is so low).

```
doug@s19:~/s19-diag$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 400000
max locked memory       (kbytes, -l) 65536
max memory size         (kbytes, -m) unlimited
[COLOR="#FF0000"]open files                      (-n) 131072[/COLOR]
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 400000
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

EDIT: I think that any ulimit can result in the "Resource temporarily unavailable" error, with the indicator being the prefix. So in your case, I think it is the open files limit. Sorry for the threads limit distraction, as it would have had a "bash fork: retry:" prefix.

---

### Post by NotQuiteSU on 2022-04-21
My script wasn't running per say, but I'm still having that error while running commands from the script. The mounted shares are all my media, so there are a LOT of files. 

The script does a find on multiple shares, so it is querying them all.

---

### Post by NotQuiteSU on 2022-04-21
ran  ulimit -n 200000

and tried again. No luck

---

### Post by NotQuiteSU on 2022-04-21
Interestingly enough, I think it has nothing to do with my script. I think that just alerts me. One of my other apps start dumping an error yesterday afternoon.  So something else is causing the issue, but I only know it when my script or this app throw an error

---

### Post by Doug S on 2022-04-21
Well, at this point we would need some better details to be able to try to help further.

---

