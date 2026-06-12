---
title: "PID &gt; 32768 on 32 bit machine"
date: 2012-11-28
forum: General Help
---

### Post by wilsonmak on 2012-11-28
Hi all,

Just wondering if there is a way to increase PID greater than 32768 on 32bit machine?
I try to modify the value (e.g. 65536) in /proc/sys/kernel/pid_max.  But it won't allow me to do so.

Thanks,
Wilson

---

### Post by LuciferRex on 2012-11-28
What do you mean, it won't allow you to do so?

Edit: I don't know what changing that value will do, BUT:
if it just doesn't let you save, it's because you need root privileges to edit it: 
```
gksudo gedit /proc/sys/kernel/pid_max
```

---

### Post by dcstar on 2012-11-28
> **wilsonmak said:**
> Hi all,

Just wondering if there is a way to increase PID greater than 32768 on 32bit machine?
I try to modify the value (e.g. 65536) in /proc/sys/kernel/pid_max.  But it won't allow me to do so.


There is no need to have a PID value of more than the total number of processes that you will ever simultaneously run on a machine, so changing it is basically pointless anyway.

Once the PID table is used up, it should wrap around to 0 and use whatever vacant PID values that there are available.

---

### Post by rnerwein on 2012-11-28
> **wilsonmak said:**
> Hi all,

Just wondering if there is a way to increase PID greater than 32768 on 32bit machine?
I try to modify the value (e.g. 65536) in /proc/sys/kernel/pid_max.  But it won't allow me to do so.

Thanks,
Wilson
the reason is very simple - on a 32 bit system the inode is: 2^n-1 in the range 1..32767
i will say - in a one liter bottle you can't fill 2 liter. --> overflow !

---

### Post by wilsonmak on 2012-11-28
Yes I know PID will wrap around to zero when it's bigger than 32768.  But I have a program that needs to compare two PIDs - PID B is always bigger than PID A (e.g. PID A=2345 < PID B=2456, that is normal, otherwise it's not normal).  When PID B wraps around to zero, it might have a chance PID B < PID A),  the comparison is wrong in this case.

Thanks,
Wilson

---

### Post by Vaphell on 2012-11-28
can the program be modified to test process start times too?

---

### Post by rnerwein on 2012-11-28
> **wilsonmak said:**
> Yes I know PID will wrap around to zero when it's bigger than 32768.  But I have a program that needs to compare two PIDs - PID B is always bigger than PID A (e.g. PID A=2345 < PID B=2456, that is normal, otherwise it's not normal).  When PID B wraps around to zero, it might have a chance PID B < PID A),  the comparison is wrong in this case.

Thanks,
Wilson
to zero it will never wrap around but a pid is given on the fly and is unique in the system.
you have no change by comparing the PID by greater or lower ( there are server running years with no downtime)

---

### Post by Statia on 2012-11-28
> **wilsonmak said:**
> Yes I know PID will wrap around to zero when it's bigger than 32768.  But I have a program that needs to compare two PIDs - PID B is always bigger than PID A (e.g. PID A=2345 < PID B=2456, that is normal, otherwise it's not normal).  When PID B wraps around to zero, it might have a chance PID B < PID A),  the comparison is wrong in this case.



So you need to rethink your program, because this will not work.

---

### Post by wilsonmak on 2012-12-06
There are no other choices.  Re-think the program. Thank You!

---

### Post by dcstar on 2012-12-08
> **wilsonmak said:**
> There are no other choices.  Re-think the program. Thank You!

Then MARK the thread.

---

