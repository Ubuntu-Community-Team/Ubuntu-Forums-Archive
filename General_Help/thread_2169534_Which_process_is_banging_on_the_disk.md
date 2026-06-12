---
title: "Which process is banging on the disk?"
date: 2013-08-22
forum: General Help
---

### Post by rickyseltzer on 2013-08-22
When my disk light starts blinking rapidly I want to know which program is causing all the ruckus.  All the system monitors (including conky) seem only able to tell me which process is using the CPU and Memory.

I'm pretty sure the system is not swapping as there never is any swap space used when I look. and ram is never full.

Linux ricky-sda8 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Cheesemill on 2013-08-22
Install and run iotop...
```
sudo apt-get install iotop
sudo iotop
```

---

