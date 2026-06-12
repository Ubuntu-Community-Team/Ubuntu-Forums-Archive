---
title: "How to kill a Zombie"
date: 2020-05-20
forum: General Help
---

### Post by arc- on 2020-05-20
I am still learning, and need some help. I have been trying out the ( top command ) and I saw a "zombie" so I researched it, only (1) zombie showed up in ( top ), but in the terminal I saw (2), the command I used ( ps aux | grep Z ), so I killed the first one, no problem. However, this one ( grep --color=auto Z ) will not die.  The response to everything I have tried, ends up with ( No such process ). I have tried to kill this for days. In addition to this problem, I was checking to see if I had any open ( ssh channel ) open ( ps aux | grep ssh ). Now this is were the confusion gets worse. They are the same. How could that be? See below.

```
user@mach:~$ ps aux | grep Z
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
user       1776        0.0       0.0  18328  1020 pts/7     S+       08:12   0:00    grep --color=auto Z

user@mach:~$ ps aux | grep ssh
user       1778  0.0  0.0  18328   972 pts/7    S+   08:12   0:00 grep --color=auto ssh

```
So how do I kill the ( grep --color=auto Z ) and kill or close the ( grep --color=auto ssh ) I have checked to see if I had any open "ssh channels" open, I could not find any, can't remember the command, maybe netstat?


Please help. Thanks

---

### Post by bill-ou812 on 2020-05-20
That isn't a zombie.  That is actually your running grep process process.

---

### Post by TheFu on 2020-05-20
The **grep** command in your pipe is what it is finding.

If you care, you could add a **| grep -v grep** to the end.  That would be 
**ps aux | grep Z |grep -v grep**

For interactive stuff, I don't bother.  Actually have this alias:
```
alias psg='ps -eaf | grep $*'
```
Run with
```
$ psg Z
```

---

### Post by arc- on 2020-05-20
Thanks, I am still learning.

---

### Post by arc- on 2020-05-20
Thanks, I tried it ( ps aux | grep Z |grep -v grep ) and did not see anything, thanks again.

---

### Post by Impavidus on 2020-05-20
When you run **ps aux | grep Z**, the shell starts two processes: **ps** and **grep**. **ps** list all processes (including itself and **grep**; it lists **grep --color=auto** because **grep** is actually an alias for **grep --color=auto**), passes the list on to **grep** and terminates. **grep** removes the line for **ps** from the list, but keeps the line with **grep**, prints the result in the terminal and terminates. So when you try to kill it, you can't, because it's already gone. The next time you run that command you'll see the same line, but most likely with a different PID.

Killing a zombie is a bit pointless. It's already dead. A zombie process has terminated and can even have been killed, but it still takes some memory to keep track of its exit status, to keep that available for the parent process. It will be gone after the parent process has called wait() to retrieve that exit status, but sometimes that parent process takes its time to do so.

Unless you configured your computer to run an ssh server, there shouldn't be one running.

---

### Post by arc- on 2020-05-20
Thanks, for all the details on ( ps and grep ). I was wondering how it all worked. I had to read to find out about the 'parent/child' process, Let's say the PID is 1587 = zombie, then you have to kill PID 1586, that took awhile to figure out. I am having fun learning. 
No, I have not configured my computer to run any (ssh server), I just wanted to make sure that none were open. The reason why is, I have something strange going on with my keyboard/terminal, the (tty/pst) I am going to try to post something on that today.
Thanks again for all your help.

---

### Post by TheFu on 2020-05-20
If the question for THIS thread is SOLVED, please help the community by marking it SOLVED.  Just above the first post is a "Thread Tools" button.

---

### Post by monkeybrain20122 on 2020-05-20
With slingshots?

---

