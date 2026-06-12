---
title: "All 8 processors at 100 %, very slow Ubuntu 22.04"
date: 2023-11-03
forum: General Help
---

### Post by hakelm on 2023-11-03
My Ubuntu 22.04 has suddenly become very slow. Gnome system monitor shows that all my 8 processors are running at 95-100 % with no active applications beside system monitor.
My system is an old Intel I7 with a Radeon R9 290/390 graphics card.

top gives me:
```
    PID ANVÄNDAR  PR  NI    VIRT    RES   DELT S  %CPU  %MIN      TID+ KOMMANDO 
 161426 root     -51   0       0      0      0 S  50,2   0,0  88:49.15 kidle_i+ 
 161427 root     -51   0       0      0      0 S  50,2   0,0  88:47.38 kidle_i+ 
 161430 root     -51   0       0      0      0 S  50,2   0,0  88:50.43 kidle_i+ 
 161431 root     -51   0       0      0      0 S  50,2   0,0  88:49.29 kidle_i+ 
 161433 root     -51   0       0      0      0 S  50,2   0,0  88:50.61 kidle_i+ 
 161428 root     -51   0       0      0      0 S  49,8   0,0  88:48.78 kidle_i+ 
 161429 root     -51   0       0      0      0 S  49,8   0,0  88:46.63 kidle_i+ 
 161432 root     -51   0       0      0      0 S  49,8   0,0  88:49.63 kidle_i+ 
   3250 he        20   0  505200 503320   1000 S   6,5   3,1  24:05.73 dbupdate 
 965435 he        20   0  430960 429112   1032 S   6,5   2,6  14:18.88 dbupdate 
 359123 he        20   0  457328 455480   1032 S   6,2   2,8  18:18.39 dbupdate 
1364862 he        20   0  420464 418612   1032 S   6,2   2,6  11:31.47 dbupdate 
1565188 he        20   0  417392 415548   1032 R   6,2   2,6   9:55.94 dbupdate 
2738128 he        20   0  400752 398900   1032 S   6,2   2,5   3:42.22 dbupdate 
1761549 he        20   0  414064 412216   1032 S   5,9   2,5   8:41.19 dbupdate 
2159847 he        20   0  407152 405300   1032 S   5,9   2,5   6:38.14 dbupdate 
3698445 he        20   0  390512 388660   1032 R   5,9   2,4   0:08.31 dbupdate
```

What can be wrong?
H

---

### Post by TheFu on 2023-11-03
Cannot tell from the data provided.  Did you check the system logs for warnings and errors?  Always start there first.

---

### Post by MAFoElffen on 2023-11-03
Please post the results of this posted within CODE tags:
```

echo "USER         PID %CPU %MEM COMMAND"; ps aux | sort -nrk 3,3 | head -n 10 | awk '{print $1 "         "$2 " " $3 " " $4 " " $11}'

```
That will bring back the top processes using %cpu... I really want to see what is pegging 8 cores.

Also do:
```

grep -m1 'model name' /proc/cpuinfo

```

---

### Post by Doug S on 2023-11-05
I'll copy and paste my comment from [the same question on askubuntu]("https://askubuntu.com/questions/1491404/all-8-processors-at-100-very-slow-ubuntu-22-04").

Your system appears to be throttling, based on the kidle_inject (I assume, the text seems to be truncated) times. I suggest using turbostat (linux tools common package, I think) and monitor things (such as processor temperature) with this command:

```
sudo turbostat --Summary --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 10
``` 

The big spew of stuff when tubostat starts up might reveal if there is and/or has been a thermal event.

And please provide the information asked for in the previous posts, and additionally the kernel version. Currently, I am not understanding the "kidle_i..." process name as I thought "kidle_inject" had been merged with, and replaced by, "idle_inject".

[Here is old but thorough answer I wrote about kidle_inject a few years ago.]("https://askubuntu.com/questions/1153613/ubuntu-19-kidle-inject-process")

---

### Post by TheFu on 2023-11-05
unnecessary comment.

---

### Post by Doug S on 2023-11-05
> **TheFu said:**
> Doug, that command is missing a ... er ... command.  I've never seen the "--Summary" command.
Thanks. I fixed the typo of my post above and the comment over on askubuntu.

---

### Post by TheFu on 2023-11-05
unnecessary comment.

---

### Post by ajgreeny on 2023-11-05
For others who may have the same problem please tell us how you fixed it and then please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction.
It is a great help to other users searching the forum.

---

### Post by SeijiSensei on 2023-11-05
Does the problem persist through a reboot?

---

### Post by MAFoElffen on 2023-11-05
@Doug S ---

Question: So 'kidle_idle' process are spawned by the CPU itself after an overload or overheat condition as kind of a survival mode kind of thing right? 

So then you would look for either an overheat condition (highly suspected) and, if not that, then filter out the 'kidle_idle' processes themselves to search for next highest processes that caused them?

Hmmm. Thinking.

---

### Post by Doug S on 2023-11-06
> **MAFoElffen said:**
> @Doug S ---

Question: So 'kidle_idle' process are spawned by the CPU itself after an overload or overheat condition as kind of a survival mode kind of thing right? 

So then you would look for either an overheat condition (highly suspected) and, if not that, then filter out the 'kidle_idle' processes themselves to search for next highest processes that caused them?

Hmmm. Thinking.As far as I recall, idle injection is not done by the CPU itself, but by some thermal daemon (thermald) and based on some temperature trip point. And, yes it is most probable that the root issue here is thermal. The particular method that thermald chooses for processor temperature mitigation is a function of: Processor make and model; CPU frequency scaling driver and governor; The order file "/etc/thermald/thermal-cpu-cdev-order.xml"; And likely other stuff that I am forgetting right now. Myself, I prefer CPU maximum clock frequency reduction for thermal management, and prefer to have the processor itself do it via the TCC offset method. I disable thermald.

Users can experiment with idle injection themselves via sysfs, but I forget how just now. I might edit later with how.

EDIT: How to manually play with idle_injection:

Step1: Find which cooling device it is:

```
doug@s19:~/c$ grep . /sys/devices/virtual/thermal/cooling_device*/type
/sys/devices/virtual/thermal/cooling_device0/type:Fan
/sys/devices/virtual/thermal/cooling_device10/type:Processor
/sys/devices/virtual/thermal/cooling_device11/type:Processor
/sys/devices/virtual/thermal/cooling_device12/type:Processor
/sys/devices/virtual/thermal/cooling_device13/type:Processor
/sys/devices/virtual/thermal/cooling_device14/type:Processor
/sys/devices/virtual/thermal/cooling_device15/type:Processor
/sys/devices/virtual/thermal/cooling_device16/type:Processor
/sys/devices/virtual/thermal/cooling_device17/type:[COLOR="#FF0000"]intel_powerclamp[/COLOR]
/sys/devices/virtual/thermal/cooling_device18/type:TCC Offset
/sys/devices/virtual/thermal/cooling_device1/type:Fan
/sys/devices/virtual/thermal/cooling_device2/type:Fan
/sys/devices/virtual/thermal/cooling_device3/type:Fan
/sys/devices/virtual/thermal/cooling_device4/type:Fan
/sys/devices/virtual/thermal/cooling_device5/type:Processor
/sys/devices/virtual/thermal/cooling_device6/type:Processor
/sys/devices/virtual/thermal/cooling_device7/type:Processor
/sys/devices/virtual/thermal/cooling_device8/type:Processor
/sys/devices/virtual/thermal/cooling_device9/type:Processor
```So, on my test computer it is device 17. What are the setting before I start:

```
doug@s19:~/c$ cat /sys/devices/virtual/thermal/cooling_device17/cur_state
0
```So, 0% idle injection, as expected, since I don't ever actually need any thermal throttling and don't use the idle_injection method anyhow.
Now, manually set 50% injection (oh ya, I forgot 49% seems to be the max, even though max says 100):
```
doug@s19:~/c$ echo 50 | sudo tee /sys/class/thermal/cooling_device17/cur_state
[sudo] password for doug:
50
doug@s19:~/c$ cat /sys/devices/virtual/thermal/cooling_device17/cur_state
49
doug@s19:~/c$ grep . /sys/devices/virtual/thermal/cooling_device17/max_state
100
```
And then observe with some other tool (top):

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
     22 root     -51   0       0      0      0 S  56.2   0.0   3:20.64 idle_inject/1
     28 root     -51   0       0      0      0 S  56.2   0.0   3:20.97 idle_inject/2
     19 root     -51   0       0      0      0 S  50.0   0.0   3:20.81 idle_inject/0
     34 root     -51   0       0      0      0 S  50.0   0.0   3:20.31 idle_inject/3
     40 root     -51   0       0      0      0 S  50.0   0.0   3:20.32 idle_inject/4
     46 root     -51   0       0      0      0 S  50.0   0.0   3:20.31 idle_inject/5
     52 root     -51   0       0      0      0 S  50.0   0.0   3:20.80 idle_inject/6
     58 root     -51   0       0      0      0 S  50.0   0.0   3:20.63 idle_inject/7
     64 root     -51   0       0      0      0 S  50.0   0.0   3:20.87 idle_inject/8
     70 root     -51   0       0      0      0 S  50.0   0.0   3:20.31 idle_inject/9
     76 root     -51   0       0      0      0 S  50.0   0.0   3:20.32 idle_inject/10
     82 root     -51   0       0      0      0 S  50.0   0.0   3:20.30 idle_inject/11
```

---

### Post by hakelm on 2023-11-07
Please forgive my forgetfulness.
I had never heard of  [COLOR=#000000][FONT=&amp]kidle_i but when I realised what it is, a processor power throttle I took off the lid of the computer. 
The dusty innards revealed themselves and pronto the PC ran as normal. A vacuum cleaner did the rest.
H
PS How do I mark the thread as solved?[/FONT][/COLOR]

---

### Post by ajgreeny on 2023-11-07
Go to Thread Tools menu at the top and mark as **Solved** from there.

---

