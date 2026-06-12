---
title: "Weird process High RAM usage"
date: 2020-09-18
forum: General Help
---

### Post by robin-journet on 2020-09-18
Hello everyone,

I need your help because my computer uses a lot of ram (more 90%) and I can't quite understand which process uses so much. It is apparently due to the messagebus user but I don't know what to do. [ATTACH=CONFIG]286979[/ATTACH]

As you can see in the picture this process is repeted a lot of time and uses a fix amount of ram.

Thank you a lot in advance.

---

### Post by VMC on 2020-09-18
Type this from a terminal, to see what program is using up all the ram:
```
ps -e -o pid,vsz,comm= | sort -n -k 2
```

---

### Post by CelticWarrior on 2020-09-18
I bet it's some rogue Java software.

---

### Post by VMC on 2020-09-18
> **CelticWarrior said:**
> I bet it's some rogue Java software.
LOL. good catch! Never thought of actually looking at the output

---

### Post by robin-journet on 2020-09-20
It is indeed a java software process. 

4021 6776152 java
It is the only pid that I can observe with the command above.

Now that I know that it is java what can I do ?

I may kill the process but i'm sure that if I reboot the programm will restart. 

What more can I do to prevent  it from hogging all the ram ?

Thanks for all your anwsers.

---

### Post by The Cog on 2020-09-20
You need to figure out what program it is. The arguments (off screen in the above screenshot) should contain the info. The output of these two commands may help (get the PID from htop):
ps -f <PID>
pwdx <PID>

---

### Post by ajgreeny on 2020-09-20
Both top and ps commands will show you the tree of processes so may be useful to show which is the culprit process using all that runaway java.
From ***man ps***> 
To print a process tree:
          ps -ejH
          ps axjf

and
From ***man top***> 
V  :Forest-View-Mode toggle
              In  this mode, processes are reordered according to their parents and the layout of the COMMAND column resembles
              that of a tree.  In forest view mode it is still possible to toggle between program name and command  line  (see
              the `c' interactive command) or between processes and threads (see the `H' interactive command).


---

### Post by robin-journet on 2020-09-21
Thank you for you answer and your help.
I tried the first command without any success (showed only the column name). 
As for the second command, It worked !! I tried pwdx on a few of this process and it showed the same application. It is located at usr/share/elasticsearch.
Tried a few reasearch on my own but can&#8217;t really find this problem on a laptop user but more on server things. 

Here is my question : Now, I know where is located the app which uses 90 % of my ram but I still don&#8217;t know what to do to prevent this program to behave like this. Thanks in advance.

---

### Post by CelticWarrior on 2020-09-21
[https://discuss.elastic.co/t/elasticsearch-taking-all-the-memory-of-the-system/77399/4](https://discuss.elastic.co/t/elasticsearch-taking-all-the-memory-of-the-system/77399/4)

---

