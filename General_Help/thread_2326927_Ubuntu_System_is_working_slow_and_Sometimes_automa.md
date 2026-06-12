---
title: "Ubuntu System is working slow and Sometimes automatically Restart"
date: 2016-06-06
forum: General Help
---

### Post by walmikg on 2016-06-06
Hi,

We have Build ubuntu 14.04 machine.
Processor:-Intel(R) Pentium(R) CPU G3250 @ 3.20GHz
Ram       :- 8 GB

Note:- Ubuntu System is working very slow and Sometimes automatically Restart. We have already given 8 GB Ram and also create Swap partition, swap partition size is twice of Ram size. 

When i run project in STS tthat time system is hanged.
and also I used Rabbit vcs for checking project update, checkout, but sometimes option is hide.
it takes to much time. 
Please help me fix the said issue.

Walmik

---

### Post by mörgæs on 2016-06-06
Hi, welcome to the fora.

You have a processor of the Haswell family, and for these I recommend a fresh install of 16.04.

---

### Post by mastablasta on 2016-06-06
> **walmikg said:**
> 
Note:- Ubuntu System is working very slow and Sometimes automatically Restart. We have already given 8 GB Ram and also create Swap partition, swap partition size is twice of Ram size. 


at best it should be the size of RAM. and even then you only need it so large if you plan to fill up the ram and then hibernate the PC. otherwise it can be arround 4 GB. with 8 GB ram you might also want to reduce swappiness, so that RAM is used more instead of hard disk.

---

### Post by coffeecat on 2016-06-06
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by grahammechanical on 2016-06-06
If the computer is automatically restarting then you should check if the machine is over-heating. If the tasks that you are performing are CPU intensive then the temperature of the CPU may be going too high.

There are two utilities in the software centre that I use. PSensor has an indicator with a drop down menu that shows speeds & temperatures for the CPU, GPU, fans, motherboard & hard drives. System Load Indicator (indicator-multiload) has an indicator that will show CPU usage, memory usage and other things.

Regards

---

