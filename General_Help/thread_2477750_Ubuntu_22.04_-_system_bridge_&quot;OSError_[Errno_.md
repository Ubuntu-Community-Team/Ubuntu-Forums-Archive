---
title: "Ubuntu 22.04 - system bridge &quot;OSError: [Errno 24] Too many open files&quot;"
date: 2022-08-05
forum: General Help
---

### Post by eelie on 2022-08-05
Hi! Running a program called System Bridge

[https://system-bridge.timmo.dev/docs/install](https://system-bridge.timmo.dev/docs/install)

Which reports all vitals (and other system information) to a gui (and also to Home Assistant). Problem is, when I run the program, it runs fine for several hours but then stops and gives this error message

```

Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/systembridgebackend/modules/>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:     self._bridge = Bridge(self.service_changed)
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/systembridgebackend/modules/>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/zeroconf/_core.py", line 450>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/zeroconf/_utils/net.py", lin>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/zeroconf/_utils/net.py", lin>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/zeroconf/_utils/net.py", lin>
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]:   File "/home/anto/.local/lib/python3.10/site-packages/ifaddr/_posix.py", line 56, >
Jul 22 07:42:15 GC676AA-ABA-m8150n python3.10[5042]: OSError: [Errno 24] Too many open files


```

Any idea what the error "[COLOR=#24292F][FONT=ui-monospace]OSError: [Errno 24] Too many open files"[/FONT][/COLOR] means and how to suggest a fix?[COLOR=#24292F][FONT=ui-monospace]

[/FONT][/COLOR]thanks![COLOR=#24292F][FONT=ui-monospace]


[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-05
Contact the program's support team and report the bug to them.

---

### Post by eelie on 2022-08-05
thanks, it was suggested that I can perhaps increase the open file limit, for example, currently the settings are at 1024, if I increase to double, say 2048, what could happen? perhaps I can choke the system, but is 1024 a good amount and is 2048 too much? thanks

```
anto@GC676AA-ABA-m8150n:~$ ulimit -a
real-time non-blocking time  (microseconds, -R) unlimited
core file size              (blocks, -c) 0
data seg size               (kbytes, -d) unlimited
scheduling priority                 (-e) 0
file size                   (blocks, -f) unlimited
pending signals                     (-i) 15425
max locked memory           (kbytes, -l) 502296
max memory size             (kbytes, -m) unlimited
open files                          (-n) 1024
pipe size                (512 bytes, -p) 8
POSIX message queues         (bytes, -q) 819200
real-time priority                  (-r) 0
stack size                  (kbytes, -s) 8192
cpu time                   (seconds, -t) unlimited
max user processes                  (-u) 15425
virtual memory              (kbytes, -v) unlimited
file locks                          (-x) unlimited
```

---

### Post by TheFu on 2022-08-06
If a desktop program needs more than 1K files open, there's a bug.  But if you are processing lots and lots of data, say for CFD or AI workloads, go for it.

The total number of files that an OS can have open is shared across the entire OS.  Allowing this 1 program more than reasonable numbers takes away from other programs.  This limit can be altered by the fs.file-max and fs.nr_open  kernel parameters in the  /etc/sysctl.conf file.  Running an OS is about sharing hardware resources in a way that works for the best outcome.

---

### Post by eelie on 2022-08-06
thanks, Fu. that makes sense.

This system could be doing lots already, for example, is my MQTT broker, handling things from 15 devices, that are probably thousands of topics a second/minute, plus its also my influxDB computer (database), I wonder if its just a matter of say there already 800 files opened, and this program needs another 800, and thus the limit is reached.

I might try to simple increase the value to 2048 just once, and just see what happens, and if it continues to crash, I know that is is truly is a bug. 

may I ask, how do I actually test this theory and increase the limit?

when I nano into [COLOR=#000000]/etc/sysctl.conf 

I don't see the entries [/COLOR][COLOR=#000000] fs.file-max and fs.nr_open, so I presume I have to type them in and then restart the system?[/COLOR]

---

### Post by Doug S on 2022-08-06
The file to edit is /etc/security/limits.conf.

The default maximum number of open files is ridiculously low, even for a decade ago.
I set it to 131072.

Here is my diff from original (including an unrelated change to maximum threads):```
doug@s19:~/config/etc/security$ diff -c limits.conf.20.04.original limits.conf
*** limits.conf.20.04.original  2019-12-24 10:31:28.993399251 -0800
--- limits.conf 2021-02-12 23:13:46.100811877 -0800
***************
*** 1,5 ****
--- 1,11 ----
  # /etc/security/limits.conf
  #
+ # S18 specific edits. 2021.02.12
+ #     increase max number threads, again.
+ #
+ # S18 specific edits. 2019.12.24
+ #     also for a rediculous number of threads test.
+ #
  #Each line describes a limit for a user in the form:
  #
  #<domain>        <type>  <item>  <value>
***************
*** 25,40 ****
--- 31,50 ----
  #        - fsize - maximum filesize (KB)
  #        - memlock - max locked-in-memory address space (KB)
  #        - nofile - max number of open file descriptors
+ * - nofile 131072
+ root - nofile 131072
  #        - rss - max resident set size (KB)
  #        - stack - max stack size (KB)
  #        - cpu - max CPU time (MIN)
  #        - nproc - max number of processes
+ * - nproc 400000
  #        - as - address space limit (KB)
  #        - maxlogins - max number of logins for this user
  #        - maxsyslogins - max number of logins on the system
  #        - priority - the priority to run user process with
  #        - locks - max number of file locks the user can hold
  #        - sigpending - max number of pending signals
+ * - sigpending 400000
  #        - msgqueue - max memory used by POSIX message queues (bytes)
  #        - nice - max nice priority allowed to raise to values: [-20, 19]
  #        - rtprio - max realtime priority
```

---

### Post by TheFu on 2022-08-06
If it isn't clear, there are 3 different limits for allowed files to be opened.

system-wide
per user
per process

It is possible to setup different numbers on each process.  That would be my initial thing to attempt along the don't fix what isn't broke line.  Don't mess with a system that is already working, except to the minimal require amount. That would be on 1 process.

---

### Post by eelie on 2022-08-08
thank all for this information.

I'm good with the don't fix what isn't broken, also.

If I wanted increase the open file size for the 1 process, how do I go about doing this? 

thanks!

---

