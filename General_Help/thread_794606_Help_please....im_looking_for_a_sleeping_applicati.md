---
title: "Help please....im looking for a sleeping application!"
date: 2008-05-14
forum: General Help
---

### Post by enerj86 on 2008-05-14
Hello, im new here srry if i bother...
im looking for an application with a "timer" that i configure for example (30 mins) and my pc will shut off...in this way i can leave my children watching a film without leaving the pc on all night. if someone knows i will really appreciate:)! tks 4 the help!
btw i use ubuntu 7.04

---

### Post by bumbleskull on 2008-05-14
you can use the sleep command to wait a certain amount of time before running the command

for example this would wait 30 minutes and shut down the computer

sleep 30m && shutdown

I believe you will need to run that as root, as shutdown requires root priveleges

---

### Post by Oldsoldier2003 on 2008-05-14
> **enerj86 said:**
> Hello, im new here srry if i bother...
im looking for an application with a "timer" that i configure for example (30 mins) and my pc will shut off...in this way i can leave my children watching a film without leaving the pc on all night. if someone knows i will really appreciate:)! tks 4 the help!
btw i use ubuntu 7.04

```
sudo shutdown -P +30
```

---

### Post by supersonicdarky on 2008-05-14
sudo shutdown -h +30

edit: bah, too slow

---

