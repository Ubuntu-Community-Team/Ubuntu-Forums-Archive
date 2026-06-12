---
title: "Slow boot process"
date: 2006-11-03
forum: General Help
---

### Post by Zdravko on 2006-11-03
Under both Breezy, Dapper and Edgy I have a slow boot procedure. Under Breezy and Dapper I noticed that the only time-consuming task is the so called "mounting" or something like that (it was the 2nd task listed in the OK/FAIL messages). So, I end up with 1min30sec pause there. Then the rest loads fast - about 20sec. Can you help me solve the problem. I will provide you with any information you require.

---

### Post by neoflight on 2006-11-03
> **Zdravko said:**
> Under both Breezy, Dapper and Edgy I have a slow boot procedure. Under Breezy and Dapper I noticed that the only time-consuming task is the so called "mounting" or something like that (it was the 2nd task listed in the OK/FAIL messages). So, I end up with 1min30sec pause there. Then the rest loads fast - about 20sec. Can you help me solve the problem. I will provide you with any information you require.

i have the same problem with edgy...the boot time is really long...sometimes i doubt that its gonna hang... but once up and running ....its pretty stable and reliable...

---

### Post by wpshooter on 2006-11-03
Are you using a SCSI drive in your computer ?

---

### Post by neoflight on 2006-11-03
> **wpshooter said:**
> Are you using a SCSI drive in your computer ?

I think I have IDE...
BUM didnt help  that much ...

---

### Post by Zdravko on 2006-11-03
No, I use IDE HDD.

---

### Post by wpshooter on 2006-11-03
> **Zdravko said:**
> No, I use IDE HDD.

The reason I ask is because I have one system which is using a good but older SCSI drive and it does the same thing.  All of my other systems which use newer SATA drives do NOT do this.

I suspect it may be due to the age of your drive and perhaps other components as well.

P.S. - I have posed question similar to yours regarding this in the past and never really received a detailed explaintion for this behavior.

---

### Post by Zdravko on 2006-11-03
Hmm, actually my HDD is quite new. It is the newest part of the PC. All other components - mother board etc. are older.

---

### Post by zekonology on 2006-11-22
i also having the same problem. The booting process stop at system checking (check for my partition) for a long period, almost 1-3 minutes. I wonder if anyone has the solutions to speed up my edgy.

Thankss :D

---

### Post by zekonology on 2006-12-04
the caused of my edgy boot so slow was fsck forced to check my disk everytime it boot. so i edited my fstab to ignore checking.. that's all.. and my edgy takes 29 sec to boot. :D

---

