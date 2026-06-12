---
title: "Newbie vmware questions"
date: 2006-11-27
forum: General Help
---

### Post by quickk on 2006-11-27
Hi everyone, 

   I know that there is a ton of information about vmware out there, and I've been trying to read up as much as I can, but before I waste another day trying to figure this stuff out I was wondering if someone could tell me if what I wanted to do was possible.  

Basically, there is only one piece of software that is holding me from completely forgoing my windows installation.  It's called origin, and it's like excel, but geared towards scientist.  I've been running it with wine/crossover office, but it's really buggy and slow.  I installed vmware, and my program seems to run pretty good inside this environment.  After a bit of reading, I stumbled across this thread: [http://ubuntuforums.org/showthread.php?t=224212&highlight=seamless+RDP+howto]("http://ubuntuforums.org/showthread.php?t=224212&highlight=seamless+RDP+howto")
which talks about rdesktop.

So this is what I want to do:

1. Have vmware server running with winXP with remote desktop/seamless enabled
2. From my host Ubuntu machine, connect to the virtual winXP and start my windows program. 
3. Manipulate large amounts of data found on my host machine with the program running on the virtual windows XP program.  

My main concern is with step 3.  Does anyone know if copying files back and forth between the host Ubuntu and virtual WinXP is very slow?  Say I start notepad like so:

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" servername
```

will notepad be able to save to my ubuntu filesystem?   Any insight would be greatly appreciated!

Thanks!

Alexis

---

