---
title: "ld-linux.so.2 excessive memory usage"
date: 2008-04-14
forum: General Help
---

### Post by Daniel15 on 2008-04-14
Hi everyone,
 Recently, at seemingly random intervals, a process called **ld-linux.so.2** has started consuming all the memory on the system, to the point where it won't respond and I need to either try to kill the process, or reboot. I have 1 GB RAM and a 1.5 GB swap file, and it started using most of the RAM, and 100% CPU (and pushed the load average up to around 7). 

Anyone have any ideas on how to fix this?

---

### Post by gaussian on 2008-04-14
I have had this, both on my Mandriva install and Ubuntu install (I am 99% sure about latter, 100% about the former). 

Are you using Acrobat Reader version 8 by any chance? It was the culprit in my case. Solutions to the problem:
1) Not using Acrobat Reader 
or better
2) Installing package called lsb (stands for Linux Standard Base), which Acrobat will use instead of ld-linux.so.2

---

### Post by Daniel15 on 2008-04-14
Alright, thanks... I removed Acrobat Reader, I'll see if that solves the problem :)

---

### Post by macabro22 on 2008-07-05
> **gaussian said:**
> I have had this, both on my Mandriva install and Ubuntu install (I am 99% sure about latter, 100% about the former). 

Are you using Acrobat Reader version 8 by any chance? It was the culprit in my case. Solutions to the problem:
1) Not using Acrobat Reader 
or better
2) Installing package called lsb (stands for Linux Standard Base), which Acrobat will use instead of ld-linux.so.2

Nice. Where did you find out about that lsb package?

---

