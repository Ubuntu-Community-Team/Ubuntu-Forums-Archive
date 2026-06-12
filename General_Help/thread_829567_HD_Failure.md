---
title: "HD Failure"
date: 2008-06-14
forum: General Help
---

### Post by abrazafi on 2008-06-14
Hi All,

Using kubuntu 7.10 and having HD Failure ...
The system tried to repair it, automaticaly, without 
any success.
It says : try to fix your HD manualy ...
What is the command to check and fix it ?

Many thanks,
Abdon.

---

### Post by tamoneya on 2008-06-14
try this: ```
sudo hdparm -t /dev/sda
```This is assuming that the drive is /dev/sda

---

### Post by phidia on 2008-06-14
Try > e2fsck /dev/hdxor sdx if you have a sata drive the "x" would be replaced by  the actual partition number for the partition you are trying to check/repair. 
Never try to check a mounted partition so you should use a live cd and often [system rescue cd]("http://www.sysresccd.org/Main_Page") is recommended.

---

### Post by abrazafi on 2008-06-15
Many thanks ... I run knoppix and my hard hard disk is having some detection error. I think I have hardware error and I need to figure out what is my problem.

I'll keep you posted,
Abdon.

---

