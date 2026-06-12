---
title: "permanently setting niceness of a process?"
date: 2013-03-19
forum: General Help
---

### Post by Kr0nZ on 2013-03-19
I have a process (java) that I want to run at a lower niceness, currently I run 'sudo renice' on the process, but I want a way to automate it.
I tried making a script which would run 'sudo nice', but then realized that whatever process I run with this command would have that process running as root, which I dont want Java to have root on my system.

So is there any setting I can change or add that would always run a process at an adjusting nice level?
Thnx

---

### Post by GameX2 on 2013-03-19
I would like to know that trick, as well.

Thanks!

---

### Post by tgalati4 on 2013-03-19
I'm thinking out loud here.  If you started a shell with *sudo nice -1 bash* and then run your JAVA process within that shell, would it run at the same nice level as the shell?  If that is the case, then you could write a script with the required nice level.

---

### Post by Doug S on 2013-03-19
Please be aware that the actual behaviour of "nice" has changed in recent years depending on the setting of "/proc/sys/kernel/sched_autogroup_enabled".

For a bit more info see [here]("http://ubuntuforums.org/showthread.php?t=2061134&highlight=nice"), which also contains links to other references.

---

### Post by Kr0nZ on 2013-03-20
> **tgalati4 said:**
> I'm thinking out loud here.  If you started a shell with *sudo nice -1 bash* and then run your JAVA process within that shell, would it run at the same nice level as the shell?  If that is the case, then you could write a script with the required nice level.

Thanks, just what I needed.
I got the following to work as I wanted
```
cmd=`echo "/usr/bin/java $tmp" | sudo nice -n -10 bash -c 'su -lm demon'`
```



> **Doug S said:**
> Please be aware that the actual behaviour of "nice" has changed in recent years depending on the setting of "/proc/sys/kernel/sched_autogroup_enabled".
For a bit more info see [here]("http://ubuntuforums.org/showthread.php?t=2061134&highlight=nice"), which also contains links to other references.
Thanks, I think I might have to use 'schedtool' instead?

---

