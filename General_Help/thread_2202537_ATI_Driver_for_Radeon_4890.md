---
title: "ATI Driver for Radeon 4890"
date: 2014-01-29
forum: General Help
---

### Post by david153 on 2014-01-29
Hi,

Fresh installed of Ubuntu 13.10. I have installed the ATI binary X.Org driver but my fan speed on my ATI Radeon 4890 is still really fast and is rather annoying due to how loud it is at speed. I tried:

david@ubuntu:~$ sudo amdconfig --initial
amdconfig: No supported adapters detected

But didn't work as per error above... 

I also tried this: 

david@ubuntu:~$ sudo amdconfig --initial
amdconfig: No supported adapters detected

No avail. Any help much appreciated.

---

### Post by ajgreeny on 2014-01-29
There is no Linux driver from ATI for the 4xxx range of graphic cards any more, so you will need to remove any that you have tried installing and settle for the open source version that was used right after installing 13.10, I'm afraid.

---

### Post by david153 on 2014-01-29
> **ajgreeny said:**
> There is no Linux driver from ATI for the 4xxx range of graphic cards any more, so you will need to remove any that you have tried installing and settle for the open source version that was used right after installing 13.10, I'm afraid.

When I rebooted I was greeted by the incompatible driver screen so had to remove... For anyone interested the command I used was: [FONT=Ubuntu Mono]sudo apt-get purge fglrx*

So version 13.10 of ubuntu already comes with a driver for my graphics card or there is an open source version that I can download for 13.10? Not really sure what you mean.. I just need a way to slow down my graphics card fan [/FONT]:(

---

### Post by ajgreeny on 2014-01-30
What I mean is that there is no need to download any driver for your card after installing Ubuntu; the open source driver is all that is available and is being used by the system from the start.

I am sorry but I have no information on how to stop your graphic card fan form running full speed all the time.

---

