---
title: "Ubuntu Randomly Freezes PLEASE HELP"
date: 2006-12-27
forum: General Help
---

### Post by tigafan09 on 2006-12-27
I'm running Ubuntu 6.10 and installed it from the alternate cd. Before I started the text install I pressed F6 and added all-generic-ide and irqpoll to the list. Ubuntu will randomly freeze I have no idea what's causing it but when it freezes the whole system freezes I can't even move the mouse.
My computer hardware:
Intel Core 2 Duo E6600
Asus P5W DH Deluxe Motherboard
ATI X1950 XTX Video Card
2x 1GB Corsair CM2X1024-6400C4 DDR2 RAM

Please help me! This problem is driving me crazy! I don't think it's bad hardware because my computer runs Windows perfectly (I'm in it now).
Thanks

---

### Post by dbbolton on 2006-12-27
is there possibly a defect with the disc ?

---

### Post by tigafan09 on 2006-12-27
install disk?

---

### Post by astrobit on 2006-12-27
i had the same freezing problem but it was caused by an overheating of the system.
i added a new kickass heat disipator and the problem is gone :D

---

### Post by ~LoKe on 2006-12-27
Overheating can cause some funky problems.

---

### Post by viper on 2006-12-27
> **tigafan09 said:**
> install disk?

Could be, or you might have a hardware issue.
Have you tried the live cd to at least rule out the hardware side ?

---

### Post by viper on 2006-12-27
Just thought could be a memory problem. Run the mem check tool b4 you run the live cd.

---

### Post by ~LoKe on 2006-12-27
> **viper said:**
> Just thought could be a memory problem. Run the mem check tool b4 you run the live cd.

Rather than sit waiting for the memtest to complete, just pull out one of the sticks of ram.  If the problem still occurs, put it back in and pull out the other one.

---

### Post by viper on 2006-12-27
> **~LoKe said:**
> Rather than sit waiting for the memtest to complete, just pull out one of the sticks of ram.  If the problem still occurs, put it back in and pull out the other one.

Good point.

---

### Post by tigafan09 on 2006-12-27
overheating sounds like itd be the most possible thing... is there any way i can tell if thats the problem before i go out and buy stuff? what heat disipator did you buy?
I will try pulling the mem sticks out one at a time too

---

### Post by ~LoKe on 2006-12-27
> **tigafan09 said:**
> overheating sounds like itd be the most possible thing... is there any way i can tell if thats the problem before i go out and buy stuff? what heat disipator did you buy?
I will try pulling the mem sticks out one at a time too

Got one of those big-*** desk fans?  Open up the side of your case and put the fan on the ground and point it at your processor on an angel (kind of pointing to the back), this helps with airflow.  Then see if you have the problem.

---

### Post by tigafan09 on 2006-12-27
i un-overclocked my cpu to drop down the temp a bit to see if that would help... didn't
so i pulled one of the ram sticks out... is working pretty good so far! i'm actually posting from it now! hopefully it wont be freezing soon

---

### Post by ~LoKe on 2006-12-27
Just so you know, the term is "underclock". ;)  But yeah, ram modules can sometimes do odd things.  Based on the specs, I assume it's considerably new.  Is it a Dell?  Custom built system?

I'd RMA is as soon as possible if you can.

---

### Post by rykel on 2006-12-27
> **tigafan09 said:**
> Ubuntu will randomly freeze I have no idea what's causing it but when it freezes the whole system freezes I can't even move the mouse.

I personally suspect that your problem lies with the ext3 filesystem. Try using ReiserFS for a change... I suspect ext3 is now doing to my laptop exactly what it is doing to yours after barely 3 months of running Edgy... whole system hangs, and only a HARD SWITCH TURN OFF will reset the unit.   :mad: 

For your information (fyi), I once had at least 2 desktop hard disk that I believe were destroyed by Fedora and ext3, and they were fresh installs.

---

### Post by ~LoKe on 2006-12-27
Isn't the ReiserFS risky when dealing with large files, or am I thinking or something else?

---

