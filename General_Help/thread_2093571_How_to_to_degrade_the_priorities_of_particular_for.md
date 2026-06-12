---
title: "How to to degrade the priorities of particular foreground processes?"
date: 2012-12-11
forum: General Help
---

### Post by csiko on 2012-12-11
It looks like the commands nice/renice have no effect between processes started as foreground process and processes started as background processes. Even with maximum niceness on the foreground processes they get always more attention. While this makes a lot of sense for processes where the user is waitung for the result, it becomes a problem if a long running process is started that way. I thought that Linux should de-prioritize (make slower) long running tasks, but according to the below example, this is not the case: user_foo started all processes as foreground processes, they run now for several weeks. The recently started background tasks of user_bar (they would potentially also use 100% of a CPU if they could) are scheduled with lower priority, despite having niceness -20.

```

  top - 17:12:27 up 31 days,  8:29,  4 users,  load average: 33.04, 32.60, 29.48
  Tasks: 278 total,  26 running, 252 sleeping,   0 stopped,   0 zombie
  Cpu(s): 91.6%us,  0.8%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  7.5%st
  Mem:  16434608k total, 15893028k used,   541580k free,  1168920k buffers
  Swap: 24673276k total,    18100k used, 24655176k free,  2255512k cached
  
    PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
   2399 user_foo  39  19 4117m 246m  60m S  102  1.5  34915:56 heavytask
   2234 user_foo  39  19 4052m 201m  59m S  101  1.3  39631:48 heavytask
   3474 user_foo  39  19 4674m 1.1g  58m S  100  7.2  36057:58 heavytask
   3782 user_foo  39  19 4447m 1.3g  58m S  100  8.5  36108:42 heavytask
   3128 user_foo  39  19 3112m 182m  60m S  100  1.1  29983:33 heavytask
   6644 user_foo  39  19 3637m 705m  59m S  100  4.4  26310:45 heavytask
   2571 user_foo  39  19 5220m 1.8g  60m S   99 11.7  14908:44 heavytask
  14607 user_bar   0 -20 52488  12m 5368 R   84  0.1  10:42.24 otherTASK
  14755 user_bar   0 -20 52488  12m 5368 R   82  0.1  10:35.85 otherTASK
  14758 user_bar   0 -20 52488  12m 5368 R   78  0.1  10:54.96 otherTASK
  14795 user_bar   0 -20 52488  12m 5368 R   76  0.1  10:01.66 otherTASK
  14783 user_bar   0 -20 52488  12m 5368 R   75  0.1   9:32.76 otherTASK
  14596 user_bar   0 -20 52488  12m 5368 R   30  0.1  10:40.58 otherTASK
  14728 user_bar   0 -20 52488  12m 5368 R   30  0.1   9:39.03 otherTASK
  14583 user_bar   0 -20 52488  12m 5368 R   27  0.1  10:07.11 otherTASK
  14706 user_bar   0 -20 52488  12m 5368 R   26  0.1   9:38.22 otherTASK
  14501 user_bar   0 -20 52488  12m 5368 R   25  0.1   9:40.70 otherTASK

```What can be done to degrade the priority of these particular  foreground processes? (or to elevate the priority of particular  background processes)?
  (System is Ubuntu 12.04 LTS with Kernel 3.2.0-32)

---

### Post by Cheesehead on 2012-12-11
You seem to have the nice levels reversed.
-20 is 'most favorable scheduling' - highest priority.
+20 is 'least favorable scheduling' - lowest priority.

---

### Post by Doug S on 2012-12-11
There were some recent (last couple of years) kernel changes with respect to how nice works. You might want to try:```
sudo sysctl kernel.sched_autogroup_enabled=0
```See also [here]("http://ubuntuforums.org/showthread.php?t=2061134&highlight=nice") and [here]("http://serverfault.com/questions/405092/nice-level-not-working-on-linux").

---

