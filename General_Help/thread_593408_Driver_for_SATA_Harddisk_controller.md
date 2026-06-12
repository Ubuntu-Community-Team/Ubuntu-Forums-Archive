---
title: "Driver for SATA Harddisk controller"
date: 2007-10-27
forum: General Help
---

### Post by Mullerkras on 2007-10-27
For some years I have had XP and Ubuntu running on my computers and used dual boot. This has workeds perfectly well and without any problem.

However, after bying a new PC (Medion) with Wista I can no longer install  Ubuntu as the intallation stops when I come to the point where I shall choose which hard disk or partition to install Ubuntu. There is no choice here. Medion says it could be that a Linux driver is missing in the harddisk controller. 

I have not been able to find a satisfactory answer on the Internet or a good explanation here to other similar questions even if I can see, that more people have the same problem. Is it really true that nobody knows how to fix this problem? Is it UBUNTU that does not have the missing driver on the installation DVD or has it something to do with the choice of harddisk?

I have no technical expirience and hope there is someone here that can help me. 

Thank you in advance.:confused:

---

### Post by chrisccoulson on 2007-10-27
What controller is it? What is the output of dmesg as run from the live CD?

---

### Post by Mullerkras on 2007-10-27
I regret to let you know that I even do not know how the harddisk controller looks or where it is placed in the computer. I have no technical knowledge.

Is it possible that you can tell me if such drivers normally will be included in UBUNTU's installation DVD and if the problem is that some harddisks do not support LINUX? I would like to understand why I have this problem.

Thanks for your help

---

### Post by chrisccoulson on 2007-10-27
From the live CD, could you post the output of:
```
lspci -v
```

Do you know the model of your motherboard?

---

### Post by Mullerkras on 2007-10-27
I can see that I need to open the computer and look for the asked information. Unfortunately, this is not possible at the moment. However, I shall be back later and hope you are still there.

Thank you for your kind assistance

---

### Post by chrisccoulson on 2007-10-27
The output from lspci -v may be enough. But knowing your motherboard model will be useful, as there may be other users with same hardware who have had similar problems, and may be able to offer assistance

---

### Post by rbmorse on 2007-10-27
If you don't want to open the case, if you can tell us what model Medion you have we can devine the specifics of the motherboard

---

### Post by Mullerkras on 2007-10-28
This is the information that I have:

MEDION: PC MT8
Typ: MED MT 457
Input max: AC230-240V-3A 50Hz
MED S/N 14499010040652
4490 01 MED DK
Art-Nr 10010253
MD 8822-Serial Number: 4499 01

Thank you for your kind assistance

---

### Post by seventyeights on 2007-10-28
Is this your computer?
[http://www.onlinekosten.de/news/artikel/24785]("http://www.onlinekosten.de/news/artikel/24785")

---

### Post by Mullerkras on 2007-10-29
Yes, this is my computer. I have bought it here in Denmark.

---

### Post by MegaWatty on 2008-01-22
You are not alone!!!

[http://ubuntuforums.org/showthread.php?t=609561](http://ubuntuforums.org/showthread.php?t=609561)

---

### Post by pkapcin on 2008-01-22
need to know what is in your PC.  I used this...   [http://www.4allmemory.com/](http://www.4allmemory.com/)   ... I'll look for my other source...

---

