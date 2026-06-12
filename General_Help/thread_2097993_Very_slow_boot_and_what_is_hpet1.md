---
title: "Very slow boot and what is hpet1"
date: 2012-12-25
forum: General Help
---

### Post by edyp87 on 2012-12-25
Hello,

I’ve got a problem with very slow Ubuntu 12.10 boot on my Asus laptop. It just hangs on for two minutes after grub . After these two minutes everything is working fine. This problem occurs since Ubuntu 10.10, 10.04 is working fine.

 I can see these entries in dmesg:

> 
[   10.280717]  [<c15d1c7e>] ? kernel_thread_helper+0x6/0x10
[   10.280724]  ---[ end trace b1793aea6dcc568d ]---
[  149.816216] hpet1: lost 117715576 rtc interrupts
[  149.816236] INFO: rcu_sched self-detected stall on CPU { 0}  (t=37231 jiffies)


Can you tell me what is the source of this issue and how can I solve it?

---

### Post by rnerwein on 2012-12-25
> **edyp87 said:**
> Hello,

I’ve got a problem with very slow Ubuntu 12.10 boot on my Asus laptop. It just hangs on for two minutes after grub . After these two minutes everything is working fine. This problem occurs since Ubuntu 10.10, 10.04 is working fine.

 I can see these entries in dmesg:



Can you tell me what is the source of this issue and how can I solve it?
hi
about your question: 3 * 9 = google

cheers

---

### Post by 2F4U on 2012-12-25
HPET is a hardware timer:

[http://en.wikipedia.org/wiki/High_Precision_Event_Timer](http://en.wikipedia.org/wiki/High_Precision_Event_Timer)

The dmesg output is kind of useless because it has no timestamps. I would suggest you get the part from syslog that covers the hang and hopefully this shows on what it is waiting.

---

### Post by edyp87 on 2012-12-25
Thanks for your reply. 

> **2F4U said:**
> The dmesg output is kind of useless because it has no timestamps.

Timestamps are included between brackets in dmesg output. 
Thanks for your answer about hpet. I've added "hpet=disable" option to grub2 config file and I am testing it now. I think that it boots without problems now.

---

