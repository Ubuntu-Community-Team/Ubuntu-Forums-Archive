---
title: "Problem outputting top command"
date: 2017-03-08
forum: General Help
---

### Post by mrmcox on 2017-03-08
Hi All,

I am running the following command
```
(echo "$(date) " && top -b -n 1 | head -n 17 | tail -n 11) >> /usr/logging/ps.log;

```

If i run it as it then I get...


Wed Mar  8 11:45:44 UTC 2017
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
    1 root      20   0   55376   5552   3560 S   0.0  0.1   1:24.97 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:02.90 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:47.36 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.70 migration/0
   10 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 lru-add-drain
   11 root      rt   0       0      0      0 S   0.0  0.0   0:01.40 watchdog/0
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0

Which format wise is great but is missing a load of processes at the top of the list. If I remove the '-b -n 1' from the command I get...

$
Wed Mar  8 11:49:05 UTC 2017
^[[7m  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                $
^[(B^[[m 1604 root      20   0  435856  19708   4040 S   6.7  0.5  12:32.51 dockerd                                                                                                                             $
^[(B^[[m    1 root      20   0   55376   5552   3560 S   0.0  0.1   1:24.99 systemd                                                                                                                             $
^[(B^[[m    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd                                                                                                                            $
^[(B^[[m    3 root      20   0       0      0      0 S   0.0  0.0   0:02.91 ksoftirqd/0                                                                                                                         $
^[(B^[[m    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                                                                        $
^[(B^[[m^[[1m    7 root      20   0       0      0      0 R   0.0  0.0   0:47.38 rcu_sched                                                                                                                      $
^[(B^[[m    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                                                                              $
^[(B^[[m    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.70 migration/0                                                                                                                         $
^[(B^[[m   10 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 lru-add-drain                                                                                                                       $
^[(B^[[m   11 root      rt   0       0      0      0 S   0.0  0.0   0:01.40 watchdog/0 

 

This includes more processes at the top of the list but also a load of weird characters at the start. 

I can probably live with the weird characters but i am concerned that with out those switches top will run forever and not end its process.

Any advice would be great.

Thanks.

---

### Post by steeldriver on 2017-03-08
How did you determine that the output is missing a lot of processes? remember that top only provides snapshots of whatever processes happen to be consuming the most resources at a specific instant

Regardless, I'd change

```

echo "$(date) "

```

to simply

```

date

```

---

### Post by vasa1 on 2017-03-08
Why are you writing the output to root?

I ran```
(echo "$(date) " && top -b -n 1 | head -n 17 | tail -n 11) >> ~/ps.log
```
and this is what I got:```
Wed Mar  8 19:24:42 IST 2017 
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
29369 vasa1     20   0  607064  27724  21444 S   6.2  0.7   0:01.82 pcmanfm
29560 vasa1     20   0   41828   3748   3200 R   6.2  0.1   0:00.01 top
    1 root      20   0  119632   5860   4056 S   0.0  0.1   0:02.16 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.33 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:07.51 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 migration/0
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 watchdog/0
```

---

