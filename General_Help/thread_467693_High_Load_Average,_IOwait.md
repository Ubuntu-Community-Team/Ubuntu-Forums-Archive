---
title: "High Load Average, IOwait"
date: 2007-06-08
forum: General Help
---

### Post by andrewPCT on 2007-06-08
Over the past week or so, I have constantly seen the CPU showing an IOwait of around 50%, and a load average of 2.00+.

Is there any way to tell what is causing this, or better, how to fix it?

---

### Post by Mr. C. on 2007-06-08
I/O wait is the measure of devices waiting for I/O to complete (such as a disk write).  There isn't enough data in your description to give any analysis.

For a quick look at what processes are up to, use

```
top -d 1
```

and watch the top processes.  Which are the top processes?

MrC

---

### Post by andrewPCT on 2007-06-08
For the most part, Xorg, metacity, other programs I am currently running are occasionally on top for a second or two at a time, then it continues with:

    1 root      18   0  2908 1860  532 S    0  0.1   0:00.94 init               
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    8 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/0           
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
...

---

### Post by Mr. C. on 2007-06-08
There is nothing interesting there.

You'll have to watch what is running when the problem is occurring.  

Have a look at the output from sar -A and spend some time becoming familiar with what it is reporting.

If your system is responsive, and working correctly, don't be concerned about run averages and I/O waits.  Run average is a marginally useful number, and I/O wait is normal for (slow) devices.

MrC

---

### Post by andrewPCT on 2007-06-08
Mr. C.

Thanks for your help.  Your mention of slow hardware helped to solve the problem.  I had a memory card reader connected (Fujifilm FinePix DPC-R1).  After disconnecting it and rebooting, the problem has gone away.

---

### Post by Mr. C. on 2007-06-08
Great!

---

