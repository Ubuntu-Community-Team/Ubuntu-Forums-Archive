---
title: "zombi Process"
date: 2017-06-09
forum: General Help
---

### Post by aminbaik on 2017-06-09
Hello,
every time I open ssh on server it's give this error:
 => / is using 89.8% of 33.52GB
  => There is 1 zombie process.

how I can know know which process is zombie ?
I try a top command and I see all services are show in are normal.
thanks.

---

### Post by Bashing-om on 2017-06-09
aminbaik; Hello;

I find the zombies from terminal:
run:
```

ps aux | grep 'Z'
pstree -p -s 20967
sudo kill 20966

```
where here 20967 is the PID of the parent and
20966 is the child that is the target in this example.

Be aware 'top' also has the ability to kill zombie processes :
[http://tecadmin.net/understanding-linux-top-command-results-uses/#](http://tecadmin.net/understanding-linux-top-command-results-uses/#)
[https://linuxaria.com/howto/understanding-the-top-command-on-linux](https://linuxaria.com/howto/understanding-the-top-command-on-linux)

[INDENT]all in the care and feeding of your 'buntu
[/INDENT]

---

### Post by aminbaik on 2017-06-09
Hello,
I run the command it's give me:
22460  0.0  0.0  12224   924 pts/0    S+   00:44   0:00 grep --color=auto Z
every time I kill it its appear again.
so what this command is do ?
thanks.

---

### Post by Bashing-om on 2017-06-09
aminbaik; Hey;

That last is the result from grep ( -color=auto). There is no zombie at that time.
My result with no zombie processes :
> 

sysop@x1604:~$ ps aux | grep 'Z'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
sysop    13127  0.0  0.0  14224   936 pts/1    S+   16:03   0:00 grep --color=auto Z
sysop@x1604:~$ 

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]all in that process of learning
[/INDENT][/INDENT]

---

### Post by aminbaik on 2017-06-09
sorry I didn't understand your answer.
what this command is do ? 
also how I cane locate the zombie in   my case ?
thanks.

---

### Post by Bashing-om on 2017-06-09
aminbaik; Hey !

Post the result of:
```

ps aux | grep 'Z'

```
And we have a discussion .
Presently you do not show to have a zombie process .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

