---
title: "Sudden but clean shutdown"
date: 2007-05-04
forum: General Help
---

### Post by buttari on 2007-05-04
Hi,
yesterday, when I was using my laptop, the system all of a sudden did a clean shutdown. By clean I mean that it correctly closed the applications and shutdown the machine. Looking at the ACPI log I found this:

```

[Thu May  3 22:29:20 2007] received event "thermal_zone THM0 000000f0 00000001"
[Thu May  3 22:29:20 2007] notifying client 5076[107:114]
[Thu May  3 22:29:20 2007] notifying client 5246[0:0]
[Thu May  3 22:29:20 2007] completed event "thermal_zone THM0 000000f0 00000001"
[Thu May  3 22:29:20 2007] received event "processor CPU0 00000080 00000003"
[Thu May  3 22:29:20 2007] notifying client 5076[107:114]
[Thu May  3 22:29:20 2007] notifying client 5246[0:0]
[Thu May  3 22:29:20 2007] completed event "processor CPU0 00000080 00000003"
[Thu May  3 22:29:20 2007] received event "processor CPU1 00000080 00000003"
[Thu May  3 22:29:20 2007] notifying client 5076[107:114]
[Thu May  3 22:29:20 2007] notifying client 5246[0:0]
[Thu May  3 22:29:20 2007] completed event "processor CPU1 00000080 00000003"
[Thu May  3 22:29:26 2007] exiting

```

does this mean that the shutdown was due to too high temperature? 
If this is the case I'd be worried because I was just browsing...
Thanks

Alfredo

---

### Post by Theimon on 2007-05-05
Looks like it indeed got overheated. Laptops generally clock themselves down when they get heated but yours apparently shuts down to prevent any damage.
Try to keep some room under the laptop when you're working on it. And maybe try to get some dust out as well to get a better airflow. But take caution when opening up a laptop, if you don't know what you're doing, you might break something. Get someone else to do it for you (I know I would ;) it's a rotten job)

---

### Post by buttari on 2007-05-05
> **Theimon said:**
> Looks like it indeed got overheated. Laptops generally clock themselves down when they get heated but yours apparently shuts down to prevent any damage.
Try to keep some room under the laptop when you're working on it. And maybe try to get some dust out as well to get a better airflow. But take caution when opening up a laptop, if you don't know what you're doing, you might break something. Get someone else to do it for you (I know I would ;) it's a rotten job)

Thank you Theimon. I'll try to follow your suggestions.

Alfredo

---

