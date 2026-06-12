---
title: "Limiting CPU Usage by user"
date: 2014-02-24
forum: General Help
---

### Post by bluestreek on 2014-02-24
I have tried researching this question as much as I can but I cannot seem to find the answer. I am running multicraft and I want to make sure that a broken configuration cannot use 100% of the cpu time. The PID changes each time so is there some way I can add the java start command to limit each process to only use two cpu cores. I don't want to set it to say core 0,1 I want it to just never been able to use more than 2 doesn't matter which because serveral servers start with the same config file.

[start] 
command = "{JAVA}" -server -jar nogui

This is what the command looks like in the start config. Is there something I can add to do what I want? Each server is run under a seperate user so is it possible to limit these users? I had one guy install a bitcoin miner and it used 100% cpu.

Thanks!

Edit: I also read about the java security manager but I cannot seem to find much information on it.

---

### Post by SeijiSensei on 2014-02-24
Per-user limits are usually set in /etc/security/limits.conf.  However the only relevant option I see there is a ceiling on total CPU time.  I don't think it's feasible to limit by percentage of CPU since many tasks can pin the CPU for a brief interval.  (On modern multi-core machines that happens less often.  Run the command "top" at the prompt and hit "1" when the list of jobs appear.  This will show the load on each of the virtual CPUs.)  

You could impose priority limits on your users.  Run the command 
```
info coreutils 'nice invocation'
```
for details on priorities.

---

