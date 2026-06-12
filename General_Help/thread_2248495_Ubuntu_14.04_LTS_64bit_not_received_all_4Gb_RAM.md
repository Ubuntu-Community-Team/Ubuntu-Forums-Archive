---
title: "Ubuntu 14.04 LTS 64bit not received all 4Gb RAM"
date: 2014-10-15
forum: General Help
---

### Post by andyhuynh on 2014-10-15
My computer has 4GB of RAM in the bios it shows correct 4gb.Win XP 32 bit with 3GB of children receiving child thoi.Nen 64 bit Ubuntu to recognize all 4GB of RAM. But the installation is complete, to see that a 64bit OS can only get 2,9Gib RAM, what is happening?

---

### Post by kc1di on 2014-10-15
Hello andyhuynh, 

There are a couple reasons that the ram is not being reported correctly. 
1. Could be that it's shared with you video card. 
2. bad ram you can run a memory test at boot up menu.
3. your not using the right program to see the actual ram installed.

System monitor should come close to the actual ram installed. 
you can also in a terminal type this command and it will report the amount of ram used and free.
```
free -m
```
you could also install a program from software center called "htop" which will give a pretty good readout on ram and the running processes on the machine.

Good Luck :)

---

### Post by Impavidus on 2014-10-15
[http://ubuntuforums.org/showthread.php?t=2177690](http://ubuntuforums.org/showthread.php?t=2177690)

Maybe some of the memory is taken by your graphics.

---

