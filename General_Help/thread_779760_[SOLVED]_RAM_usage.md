---
title: "[SOLVED] RAM usage"
date: 2008-05-03
forum: General Help
---

### Post by stoppage on 2008-05-03
Hi, I have a quick question on RAM usage on my Feisty installation. „KsysGuard“ tells me it's using 488MB out of 1GB, normal usage. Seems a lot, is this normal?

---

### Post by tamoneya on 2008-05-03
i am not familar with ksysguard but that is a lot for any program.  How long has it been running for.  What happens when you restart it.

---

### Post by NightwishFan on 2008-05-03
Do this command in a terminal and post the result:
```
free -m
```

---

### Post by stoppage on 2008-05-03
tony@youhits:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        468        543          0         16        272
-/+ buffers/cache:        179        832
Swap:         2502          0       2502

Restart doesnt change anything

---

### Post by sujoy on 2008-05-03
so it was cache!
actual memory use is 179MB

---

### Post by NightwishFan on 2008-05-03
Remember to use free -m and only pay attention to the +/- buffers/cache line for a good example of how much is used. :KS
Edit: You are actually running really light with ram, which is a good thing. Are you using Kubuntu?

---

### Post by stoppage on 2008-05-03
Obliged! And I'm running "Feisty"

---

