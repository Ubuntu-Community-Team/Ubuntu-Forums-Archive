---
title: "URGENT: Comp making beeping noise"
date: 2006-08-31
forum: General Help
---

### Post by eighthate on 2006-08-31
Hello my comp is making a beeping sound and my fan is making a lot of noise, it has been making this after 2 hours of turned on computer. It has been doing this everytime my computer has been turned on for more than 3 hours since a month. Some1 help me please!!

---

### Post by yopnono on 2006-09-01
Is't the CPU that makes the sound? If so try this. Put this in the "/etc/rc.local" file, and reboot.
```
echo 2 > /sys/module/processor/parameters/max_cstate
```
If you still have the noise change the "echo 2" to "echo 1" and try again.

This may fix your fan issue aswell. On some systems the CPU idle is high and that generates heat = fan on

---

