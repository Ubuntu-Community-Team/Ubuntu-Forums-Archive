---
title: "Java process gets killed?"
date: 2013-03-02
forum: General Help
---

### Post by pumpkin105 on 2013-03-02
Hi,

I have a VServer which runs Ubuntu. On that server, I have a Java application that does some calculations for me. In the last few weeks, this worked perfectly fine.
In the last few days, my Java process gets killed and/or disappears. I start the program using "nohup java -jar ...". After a few minutes writing into the database is stopped, "ps aux | grep java" doesn't show my process, the nohup output file does not show that the program has exited with an exception.

How can I find out, why my program is being killed?

Thank you

---

### Post by rnerwein on 2013-03-02
hi
i guess you got probelms with your data input for the process. if it runs in former times and stopped now. if you are familar with the shell open a terminal.
start your process ( you said it is running a few minutes ). use ps -elf | grep your_process. notice the PID. then start in the terminal:
strace -f -o bla_blu_logfile -p PID_of_the_task. will be a big output debug file (bla_blu...). java is very blithering :-(
i bet you will find - using grep: grep -i sigseg bla_blu_logfile - grep will find it. this is a hint for a excetion which is not handled in your program (your input data !).
looks for me: it's a error in the program.
ciao
[TABLE]
[TR]
[TD]
[/TD]
[TD][/TD]
[TD][/TD]
[TD="class: text"][/TD]
[/TR]
[/TABLE]

---

### Post by pumpkin105 on 2013-03-03
Thank you for your idea!

I started the program again using nohup and started strace in another terminal. While waiting for the process to stop, I pressed enter a few times until i got this message from the system: [1]+ Killed java -jar myprogram.jar
The logfile created by strace mostly contained non special lines, but there are also a few segmentation faults like you preditected. What do they mean?

---

### Post by rnerwein on 2013-03-03
> **pumpkin105 said:**
> Thank you for your idea!

I started the program again using nohup and started strace in another terminal. While waiting for the process to stop, I pressed enter a few times until i got this message from the system: [1]+ Killed java -jar myprogram.jar
The logfile created by strace mostly contained non special lines, but there are also a few segmentation faults like you preditected. What do they mean?
hi
segmentation fault is pretty normal for java programming (often quick and dirty- mostely NULL-Pointer reference). if you got a couple of them then the process has sigsegv blocked.
is there another signal which cause the process to stop. the only things you can do is to write a problem against the programmers or try to figure out which data-sentenc cause this killing exception.
sorry no more ideas
ciao
P.S. SIGSEGV means the process wants to reference an address which don't belongs to his addresspace. in words -> it's a bug

---

### Post by pumpkin105 on 2013-03-03
I get several of these:

```
20602 <... futex resumed> )             = -1 ETIMEDOUT (Connection timed out)
```

Edit:
And 99% of the logfile looks like this:

```
20607 sched_yield( <unfinished ...>
20605 sched_yield( <unfinished ...>
20607 <... sched_yield resumed> )       = 0
20605 <... sched_yield resumed> )       = 0

```

---

### Post by rnerwein on 2013-03-03
hi
futex resumed and sched_yield isn't a reason to end the process (futex is used to syncronize threads in userspace, yield is used for scheduling - changing the runqueue of the process-threads)
the reason of breaking the process must be found in the strace-log. thats why if the task crashes - it's to late to write a log message
ciao

---

### Post by pumpkin105 on 2013-03-03
I have run the combination of my program and strace again and now I have a log entry that could be a hint:

```
...
1681  <... sched_yield resumed> )       = 0
1682  sched_yield( <unfinished ...>
1681  sched_yield()                     = 0
29796 +++ killed by SIGKILL +++
1697  <... ???? resumed> )              = ? <unavailable>
29904 +++ killed by SIGKILL +++
29927 <... ???? resumed> )              = ? <unavailable>
29890 +++ killed by SIGKILL +++
29885 +++ killed by SIGKILL +++
29927 +++ killed by SIGKILL +++
29879 +++ killed by SIGKILL +++
29865 +++ killed by SIGKILL +++
29843 +++ killed by SIGKILL +++
29836 +++ killed by SIGKILL +++
29788 +++ killed by SIGKILL +++
... (about 20 more and then the log file ends)

```

What does this tell me?

---

### Post by pumpkin105 on 2013-03-04
*bump*

---

