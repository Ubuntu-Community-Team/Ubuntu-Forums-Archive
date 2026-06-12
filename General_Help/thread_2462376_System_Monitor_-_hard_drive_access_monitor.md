---
title: "System Monitor - hard drive access monitor ?"
date: 2021-05-19
forum: General Help
---

### Post by anneranch on 2021-05-19
After "upgrade" to 21.04  I hear unusual hard drives activity . 
Is there a tool likes "System Monitor"  to see this activity to determine if it is harmless or something to be concern about?

---

### Post by dragonfly41 on 2021-05-19
There is Stacer.  A nice GUI for different monitoring tasks.

---

### Post by ActionParsnip on 2021-05-19
iotop for HDD access

---

### Post by anneranch on 2021-05-19
I downloaded both. 
iotop is little cryptic 
stacer seem to be "poor man " System Monitor. 
Pretty basic on  multi cpu and seems to monitor only active HDD - currently downloading  Qt  update. 
Appreciate the reply - many thanks

---

### Post by dragonfly41 on 2021-05-19
Then try GKRellM.

---

### Post by deadflowr on 2021-05-19
Hearing things is never good.
I'd check SMART status.
You can either look at the [SMART output from Disks]("https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en") or follow [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

The disk might have had issues already, but the upgrade simply pushed it over the edge.

---

