---
title: "Question about assigning a PID"
date: 2007-03-29
forum: General Help
---

### Post by SBFC on 2007-03-29
Is it possible to launch an application and actually assign it a specific PID?

For example, I want to launch an application with cron, and after 10 minues or so, kill it. Which really depends on knowing the PID.

---

### Post by hikaricore on 2007-03-30
If it's a specific process that isn't running more than that one copy you lanuched, you can kill it like this:

```
kill -9 $(pidof -x application-name);
```

If it's something which you're running more than one copy of, you may need to write up a more complex bash script to accomplish this.

---

### Post by acormack on 2007-03-30
The key thing to remember about PIDs is that they must be unique.  

If you could do what you requested (which I doubt) it would lead to intermittent failures because sometimes the PID would conflict with another program and sometimes it wouldn't.

There are two ways to achieve the same result.

1.  Is to write a shell script called via cron which runs the program and captures the PID returned and saves it in a file which you can later use in a kill command.

2.  Is my favourite which is to use the **ps** command to find the pid of the running program and then kill it.

if the command below is run every running program  called "fred" would be killed:

kill -15 `ps -ef | grep fred | grep -v fred | awk '{print $2}'`

Please note that the exact punctuation above including the quotes are important.  Use copy and paste!

If you want me to explain why this works I will - but if you just use it - it will work.


Alec

---

### Post by SBFC on 2007-03-30
Thank you both for your replies.

> kill -15 `ps -ef | grep fred | grep -v fred | awk '{print $2}'`

Please note that the exact punctuation above including the quotes are important. Use copy and paste!

If you want me to explain why this works I will - but if you just use it - it will work.

I actually would be appreciative if you explained how that one worked. 

However, I tried it out with scite (copy/pasting, replacing 'fred' with 'scite' obviously) I received the following:

```
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
```

Whereas ```
kill -9 $(pidof -x scite);
``` did kill scite. I wouldn't mind an explanation of that one either. :P

I don't understand what the '-9' is for (or the -15 in the other one), as well as the '$' before the open paren.

---

### Post by acormack on 2007-03-30
There was a typo in my earlier post (sorry)

kill attempts to terminates programs that are running.

the parameter -15 means ask the application to close as gently as possible
the parameter -9 means die immediately whatever you are doing


If the -15 works it is normally safer.  One possibility is to run 2 commands in sequence.  The -15 first to kill the application gently if it is possible

Then the -9 to kill it if it isn't responding.



sudo kill -15 `ps -ef | grep fred | grep -v grep | awk '{print $2}'`
sudo kill -9 `ps -ef | grep fred | grep -v grep | awk '{print $2}'`

Explanation

e.g. if I have 2 copies of konsole running then 

**ps -ef | grep konsole **   

returns 3 lines

akc       5569  5413  0 19:36 ?        00:00:02 konsole [kdeinit]
akc       5718  5413  9 19:46 ?        00:00:00 konsole [kdeinit]
akc       5737  5595  0 19:46 pts/1    00:00:00 grep konsole


**ps -ef | grep konsole | grep -v grep**

returns 2 lines excluding grep

akc       5569  5413  0 19:36 ?        00:00:02 konsole [kdeinit]
akc       5718  5413  1 19:46 ?        00:00:00 konsole [kdeinit]

**ps -ef | grep konsole | grep -v grep | awk '{print $2}'**

uses the awk command to select just the second word of each line for printing
5569
5718

finally the ``   quotes tell the bash shell to treat the contents as a command to be executed

finally the kill -15 is passed the list of pids to be killed.

I hope this makes sense (and I haven't made any more typos!)


Alec

---

### Post by hikaricore on 2007-03-30
> **SBFC said:**
> Thank you both for your replies.

Whereas ```
kill -9 $(pidof -x scite);
``` did kill scite. I wouldn't mind an explanation of that one either. :P

I don't understand what the '-9' is for (or the -15 in the other one), as well as the '$' before the open paren.

Okies well obviously **kill** is the command to kill a process or service.

With all kill functions you have 31 different number levels that represent
different methods of killing said process.  9 is known as sigkill, this simply
sends the signal to kill the process.  15 is known as sigterm, as acormack
mentioned, this is used to attempt to close the process.  However I am
cruel to my processes and prefer that they just die.  Without question.  :P

What the code I gave you does, is runs the pidof command which checks
for the process id of a certain process first.  It then places the return of this
pidof check (if any exists) into the kill command and presto, dead process.

I use this method alot in my service shutdown scripts where a simple:

```
killall process
```

Fails me and I'm too lazy to open top or htop.

:)

---

### Post by stylishpants on 2007-03-31
> **acormack said:**
> 

**ps -ef | grep konsole | grep -v grep | awk '{print $2}'**



This sort of pattern can usually be replaced by a use of the 'pidof' command.


Note that pidof returns multiple pids on the same line:

```
fraser@ged:~$ ps -ef f | grep python | grep -v grep | awk '{print $2}'
6211
6635
7241
8389
24675

fraser@ged:~$ pidof python
24675 8389 7241 6635 6211

```


If this is a problem, it is easily altered with a call to "tr":

```

fraser@ged:~$ pidof python | tr " " "\n"
24675
8389
7241
6635
6211

```

---

