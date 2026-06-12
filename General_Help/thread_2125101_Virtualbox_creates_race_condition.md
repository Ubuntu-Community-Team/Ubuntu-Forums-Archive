---
title: "Virtualbox creates race condition"
date: 2013-03-13
forum: General Help
---

### Post by Kopkins on 2013-03-13
Using 12.04 64 with Kernel 3.2.0-38. Using the latest VBox in the repos. I've had several occurances of virtualbox freezing then creating a race condition. After I finally kill virtualbox and try to shut down I can't. I end up in a TTY and can't even shutdown the system. I have to hold down the power button to shutdown, which I hate doing. Is this a known issue? CPU gets to temps of 96-99 Celsius. I like virtualbox but not enough to risk frying my computer. I'm done for a while with vbox. I see that it had problems with older kernels. Is there a fix for this?

Kopkins

---

### Post by skinnymg1 on 2013-03-13
I'm not up to speed on the VBox thing but next time you cannot shutdown try this. Hit ctrl+atl+F1, log in, then enter "sudo shutdown -h now". It's never good to hold the button like that, espescially if you have mechanical hard drives in the machine.

---

### Post by deadflowr on 2013-03-13
What are the specs for the machine?

---

### Post by Kopkins on 2013-03-13
> **skinnymg1 said:**
> I'm not up to speed on the VBox thing but next time you cannot shutdown try this. Hit ctrl+atl+F1, log in, then enter "sudo shutdown -h now". It's never good to hold the button like that, espescially if you have mechanical hard drives in the machine.

I didn't have the -h flag in there. I'll try that next time. Yeah I know that's why I hate it so much. 

> **deadflowr said:**
> What are the specs for the machine?

Macbook 8,1 with i5-2415M 2-cores+hyperthread and 4GB RAM 

I don't run out of RAM when this happens.

---

### Post by rnerwein on 2013-03-13
> **Kopkins said:**
> Using 12.04 64 with Kernel 3.2.0-38. Using the latest VBox in the repos. I've had several occurances of virtualbox freezing then creating a race condition. After I finally kill virtualbox and try to shut down I can't. I end up in a TTY and can't even shutdown the system. I have to hold down the power button to shutdown, which I hate doing. Is this a known issue? CPU gets to temps of 96-99 Celsius. I like virtualbox but not enough to risk frying my computer. I'm done for a while with vbox. I see that it had problems with older kernels. Is there a fix for this?

Kopkins
hi
i think it's better to talk about a run-away process than a race-condition (wich can be the reason too).
some explanation you can (may be) see in my appendix (don't be afraid it's pure ascii).
i guess the temps of your CPU is coming from USER-mode - figure out which task(s) is (are) reponsible
ciao

---

### Post by Kopkins on 2013-03-13
> **rnerwein said:**
> hi
i think it's better to talk about a run-away process than a race-condition (wich can be the reason too).
some explanation you can (may be) see in my appendix (don't be afraid it's pure ascii).
i guess the temps of your CPU is coming from USER-mode - figure out which task(s) is (are) reponsible
ciao

If virutalbox runs away and I kill it and everything dealing with it yet my cpu is still at max what is it?

The processes that are using all the CPU are khelper. And I can't stop them. In system monitor they don't even show up and there isn't a program using more than ~2-3% CPU. The only place khelper shows up is in top. If you looked at the my system monitor everything looked fine except the CPU and RAM usage. I can't stop khelper. 

Where is your appendix?

Whatever it is, race or runaway, I don't like my fans at 6000+rpm and my cpu able to boil water.

---

### Post by Kopkins on 2013-03-14
Does anyone else have any ideas about this or a potential solution?

---

