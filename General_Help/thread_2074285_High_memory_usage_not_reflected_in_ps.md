---
title: "High memory usage not reflected in ps"
date: 2012-10-21
forum: General Help
---

### Post by mblahay on 2012-10-21
I am trying to track down what is causing my 11.10 system to report high memory usage, yet when I view my processes, the memory usage doesn't add up. I even tried using ps and free to get the memory usage by process and the numbers still don't add up.

What is happening? How do I get the correct numbers?

---

### Post by dino99 on 2012-10-21
watch also your logs.

---

### Post by efflandt on 2012-10-21
What is telling you that you are using lots of memory?  Note that in the output of "free", the Mem: line makes it look like I am using over 3 GB, but some of that is buffers and much of that is cached (previously used programs or disk data).  The +/- buffers/cache line shows that kernel and programs are actually using less that 800 KB and if necessary I have over 7 GB available.

```
efflandt@XPS8100-1204:~$ free
             total       used       free     shared    buffers     cached
Mem:       8103740    3357092    4746648          0     393132    2191024
-/+ buffers/cache:     772936    7330804
Swap:            0          0          0
```

---

### Post by Szor3n on 2012-10-21
Also note that if your computer has an integraded graphics card of any kind, even if its not being used, it may suck up to a gig of ram out of your memory pool.

---

### Post by mblahay on 2012-10-23
But my system is using a LOT of memory...

$ free 
             total       used       free     shared    buffers     cached
Mem:      24479664   20323572    4156092          0     661004    1230552
-/+ buffers/cache:   18432016    6047648
Swap:      9765884          0    9765884

And here I am only showing those processes (via manually deleting those lines that reported none) that are reporting memory usage. The numbers just don't add up

$ ps -eo %mem,pid | sort
%MEM   PID
 0.1 12837
 0.1 16269
 0.1  1805
 0.1  1946
 0.1 26668
 0.1 27741
 0.1 27760
 0.1 27777
 0.1  3172
 0.1  3270
 0.1  3511
 0.1  4597
 0.2  3266
 0.2  3685
 0.3 14148
 0.3 16044
 0.3 16287
 0.3  1817
 0.3 24904
 0.3  2938
 0.3  3224
 0.5 12823
 0.5 16083
 0.5 16296
 1.1  3128
 2.6 12786

---

### Post by Cheesemill on 2012-10-23
Use htop to look at what processes are using the most memory.

You can sort the output of htop by memory usage (hit F6 and select MEM%).

---

### Post by mblahay on 2012-10-24
The memory numbers from htop are making a little more sense, but at the same time there is a new mystery. Compiz is always a memory hog, and htop shows 3 or 4 instances of it, all with different process ID's and showing the exact same memory usage. This may account for why memory usage is being reported to be so high. Other tools are only displaying a single Compiz instance though.

Any thoughts on what is going on there? Am I seeing different threads of the same process or something like that? Is it really using 3 to 4 times the memory?

---

### Post by mblahay on 2012-10-24
[FONT=Courier New][FONT=Arial]Here is the output from htop. Below are the Compiz processes that I am questioning. I think I should only have a single process. In addition to Compiz, I have serveral other processes that look like they repeat many times.

[/FONT]
   1  [|||||                    13.5%]     Tasks: 137, 344 thr; 1 running
  2  [|||                       3.9%]     Load average: 2.88 2.92 2.92
  3  [|||                       4.6%]     Uptime: 14:14:19
  4  [||                        4.6%]
  Mem[|||||||||||||||||11215/[/FONT][FONT=Courier New]23905MB]
  Swp[                      0/9536MB]

[/FONT]  [FONT=Courier New]   PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 [COLOR=Red]3201 mblahay   20   0 3142M 2620M 32456 S  0.0 11.0  0:00.00 compiz
 3202 mblahay   20   0 3142M 2620M 32456 S  0.0 11.0  0:00.40 compiz
 3129 mblahay   20   0 3142M 2620M 32456 S  0.0 11.0  3:25.33 compiz[/COLOR]
 2867 root      39  19  893M  203M 11712 S  6.0  0.9 15:01.10 /usr/bin/java -Dfi
10068 root      39  19  893M  203M 11712 S  3.0  0.9  6:30.05 /usr/bin/java -Dfi
10069 root      39  19  893M  203M 11712 S  1.0  0.9  1:28.92 /usr/bin/java -Dfi
 2871 root      39  19  893M  203M 11712 S  0.0  0.9  0:01.83 /usr/bin/java -Dfi
 2872 root      39  19  893M  203M 11712 S  0.0  0.9  0:01.01 /usr/bin/java -Dfi
 2873 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.96 /usr/bin/java -Dfi
 2874 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.99 /usr/bin/java -Dfi
 2875 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.95 /usr/bin/java -Dfi
 2876 root      39  19  893M  203M 11712 S  0.0  0.9  0:03.25 /usr/bin/java -Dfi
 2877 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.07 /usr/bin/java -Dfi
 2878 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.20 /usr/bin/java -Dfi
 2879 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.00 /usr/bin/java -Dfi
 2880 root      39  19  893M  203M 11712 S  0.0  0.9  0:03.92 /usr/bin/java -Dfi
 2881 root      39  19  893M  203M 11712 S  0.0  0.9  0:03.54 /usr/bin/java -Dfi
 2882 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.00 /usr/bin/java -Dfi
 2883 root      39  19  893M  203M 11712 S  0.0  0.9  0:23.98 /usr/bin/java -Dfi
 2920 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.00 /usr/bin/java -Dfi
 2921 root      39  19  893M  203M 11712 S  0.0  0.9  0:00.00 /usr/bin/java -Dfi[/FONT]

---

### Post by mblahay on 2012-10-26
Any body have any thoughts?

---

