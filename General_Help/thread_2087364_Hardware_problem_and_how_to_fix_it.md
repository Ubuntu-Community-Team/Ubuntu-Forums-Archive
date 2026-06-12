---
title: "Hardware problem and how to fix it"
date: 2012-11-23
forum: General Help
---

### Post by spartak2012 on 2012-11-23
This message I get when I start Ubuntu 12.10 64bit
```
Hardware error 
CPU1 Machine Checkexception :4 Bank 0:b60da0009b000 135
TSC 2d0f5ce1e5 ADDR 1c18e00
POCESOR 2 : 100f22 TIME 1353601399 SOCKET 0 APIC microcode 1000065
Run the above trought 'mcelog --ascii'
Machine check Invalid
Kernel panic-not syncing:Fatal Machine check on current CPU
Shutting down cpus with NMI
Panic occured, switching back to text console
```And windows 7 64bit sometimes in start and sometimes when I play games or surfing display blue screen : 
[IMG]http://tinypic.com/view.php?pic=2ro2n3q&s=6[/IMG][http://tinypic.com/view.php?pic=2ro2n3q&s=6](http://tinypic.com/view.php?pic=2ro2n3q&s=6)
What is the problem and how to fix it???

---

### Post by Isamu715 on 2012-11-23
If both OSes are affected(and it seems that's the case - bluescreens and kernel panic) then I'd say it's a hardware problem. Do LiveCDs work?

---

### Post by Sergius14 on 2012-11-23
Most Hardware problems are faulty memory sticks or cooling issues.

First do a full memory test with Memtest86+

You can run it on the Ubuntu Live CD or your regular installation by selecting it.


Something like this:

[IMG]http://cloud.addictivetips.com/wp-content/uploads/2012/01/Ubuntu-Live-Disk-Menu.jpg[/IMG]

---

### Post by spartak2012 on 2012-11-24
> **Sergius14 said:**
> Most Hardware problems are faulty memory sticks or cooling issues.

First do a full memory test with Memtest86+

You can run it on the Ubuntu Live CD or your regular installation by selecting it.


Something like this:

[IMG]http://cloud.addictivetips.com/wp-content/uploads/2012/01/Ubuntu-Live-Disk-Menu.jpg[/IMG]

Memtest86+ was running today 5h and no error, cooling system is ok cpu 45C and graphic card 55C...

---

### Post by pqwoerituytrueiwoq on 2012-11-24
sounds related to the cpu, make sure the cpu HSF is attached properly and not full of dust, may need new thermal paste, are you overclocking?

---

### Post by spartak2012 on 2012-11-24
> **pqwoerituytrueiwoq said:**
> sounds related to the cpu, make sure the cpu HSF is attached properly and not full of dust, may need new thermal paste, are you overclocking?

No I'm not overclocking, I have clean all dust inside, here is the temp of computer...

---

### Post by BertN45 on 2012-11-24
Looks like a job for the repair shop.

---

### Post by pqwoerituytrueiwoq on 2012-11-24
run prime95/mprime for a few hours and see if any threads crash, use the stress test
if it crashes the cpu is unstable, probably not getting enough power, or since you are not over-clocking it is defective, could be a mobo issue/ bios over-clocking feature being set

---

