---
title: "java jvm keeps hdd from entering standby"
date: 2019-01-05
forum: General Help
---

### Post by redingo on 2019-01-05
I have two java applications (openhab2 and eq3 occu) on an ubuntu  18.04 machine that are doing some background activity. I would expect  this to happen in memory. But for both applications iotop is showing a  disk write operation approx. every second.
  
[LIST]
[*]I'm running laptop mode tools which set the filesystem parameters  and hdparm to spin down the disk even if there are changes to files and  write them later. 
[*]I moved all log files to a folder in tmpfs. 
[*]I turned off swap, as there is plenty of RAM in the machine. 
[*]With /proc/#pid#/fs I can't see any open files which would be written. 
[*]find -mmin 1 is not showing any updated files. 
[/LIST]
  As it happens for both applications the same way, I suspect that the java jvm is doing something on the disc directly.
  Behavior is the same whether I use openjdk1.8 or oracle java 10. I tried to use G1GC. That reduces garbage collection efforts but doesn't let the disc sleep, either.
  Could anyone give me a hint, what I could do to find out what is happening here?
  Thanks a lot!

---

