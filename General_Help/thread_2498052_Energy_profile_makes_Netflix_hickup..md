---
title: "Energy profile makes Netflix hickup."
date: 2024-05-28
forum: General Help
---

### Post by henk982 on 2024-05-28
Hi guys,

I recently updated to 24.04. And when I am watching Netflix it had a second of freezing every 30 seconds or so. It was on every browser (edge, firefox, brave, vivaldi). Also on the firefox .deb installation. 

What worked is setting the energy profile on Performance. On the balanced/saving option is happens. Never had this problem on 22.04.

Is the energy setting for balanced so agressive? I would be strange if my Lenovo thinkpad with 8 cores needs all its power to just watch Netflix online right? :-).

It is also on TLP. I also have to set the processor on performance. Other settings it hangs like described. 

Thanks for your ideas on this situation.

Henk.

---

### Post by currentshaft on 2024-05-28
?

---

### Post by henk982 on 2024-06-02
Hi,

Sorry for the late reaction. I replyed soon after your posted but I see now it is not saved.
I am not watching 4k, and screen resolution is 1920x1080. And how can I check the Netflix load with top or uptime command? I googled it but still do not now how to use it in this situation. 
When I look at the GUI processor use with system monitor, the CPU load is very low. 

Thanks again for your help.

---

### Post by currentshaft on 2024-06-02
The top or htop commands will show you, by default, which processes are using the most CPU. You can hit F6 to sort to it by this value or "CPU_TIME" to see the offending program.

The load average is also displayed by top, so you don't need to run the command separately. The three sets of numbers measure how busy the processor is over three periods of time. The value should be less than the number of cores your processor has (shown in htop).

In Firefox, you can also open about:processes to inspect how tabs are behaving.

Hope this leads to a clue!

---

