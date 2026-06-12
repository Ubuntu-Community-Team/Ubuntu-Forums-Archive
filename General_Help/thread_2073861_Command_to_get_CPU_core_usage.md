---
title: "Command to get CPU core usage"
date: 2012-10-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-20
What is the command to get the CPU usage of core X (preferably as a percentage)
Is there something i can cat in /sys/ like i can for the governor?

---

### Post by oldos2er on 2012-10-20
htop can do this, it shows the number of cores and their use by percentage by default.

---

### Post by pqwoerituytrueiwoq on 2012-10-20
i need to get it in a script, any idea where htop gets that info?

---

### Post by Cheesemill on 2012-10-20
If you install the sysstat package you can use the mpstat command and do a bit of awk'ery to get your value:
```
rob@arch:~$ mpstat | awk '$12 ~ /[0-9.]+/ { print 100 - $12 }'
5.29
```
The above is the total for all cores, if you want  the value for a specific core you can add the -P switch:
```
rob@arch:~$ mpstat -P 0 | awk '$12 ~ /[0-9.]+/ { print 100 - $12 }'
9.42
```

---

### Post by oldos2er on 2012-10-20
No idea, sorry.

---

### Post by pqwoerituytrueiwoq on 2012-10-20
[FONT=Courier New]mpstat -P 0[/FONT] is far from accurate
Idle:
```
Linux 3.6.2-030602-generic (Quantal-Desktop)     10/20/2012     _x86_64_    (4 CPU)

01:04:56 PM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
01:04:56 PM    0    3.70    2.05    3.04    1.38    0.00    0.07    0.00    0.00   89.75

```
prime 95 torture test:
```
Linux 3.6.2-030602-generic (Quantal-Desktop)     10/20/2012     _x86_64_    (4 CPU)

01:06:11 PM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
01:06:11 PM    0    3.81    2.21    3.09    1.31    0.00    0.07    0.00    0.00   89.51
```

---

### Post by Cheesemill on 2012-10-20
You're absolutely correct, I've just done some testing of my own and it was way off.
I'm not sure where it gets its values from then.

---

