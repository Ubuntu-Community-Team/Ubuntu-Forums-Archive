---
title: "Insatlled Ubuntu, but can't boot it"
date: 2007-10-07
forum: General Help
---

### Post by COF on 2007-10-07
Hi
I ran through the Wubi installer w/o any problems, but now when I boot it goes straight to windows XP. it just doesen't give me any booting options. Anyone know what might have gone wrong?
I was told to look at my boot.ini file, but I don't see anything wrong with it. Here it is:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect
c:\wubildr.mbr="Ubuntu"

Any suggestions?
COF

---

### Post by COF on 2007-10-11
Never mind, I fixed it by changing the timeout from 15 to 30.

---

