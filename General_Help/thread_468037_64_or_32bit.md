---
title: "64 or 32bit?"
date: 2007-06-08
forum: General Help
---

### Post by Arrowx7 on 2007-06-08
Hello,
I installed ubuntu server on a 64bit machine, is there a way to find out whether my machine is running a 32 bit or 64 bit kernel?

thanks.

---

### Post by Outrunner on 2007-06-08
```
uname -a
``` I think should give you some info.

---

### Post by Arrowx7 on 2007-06-08
what do I look for?

---

### Post by rocknrolf77 on 2007-06-08
Try ```
uname -m
```

---

### Post by k1001001 on 2007-06-08
All I got with 'uname -m' was 'i686.' Not very descriptive.

---

### Post by MaindotC on 2007-06-08
If it was 64-bit it would say x64 or something to that effect.  i686 is another type of Intel architecture.  I did a couple google searches and couldn't find anything definitive stating if it was 32/64 bit.

---

### Post by Arrowx7 on 2007-06-08
anyone else have any suggestions?

---

### Post by rocknrolf77 on 2007-06-08
sorry I can't help you anymore. I know there's a lot of people here that can help you. You just have to have some patience :) 

The things you can help other with the best, is the the same problems you ran in to yourself. (And found a solution off course) Take a look around while you wait and maybe help someone that ran in to the same problems you had, and help them out. Maybe they have an answer to your problems.

What come around go around :)

---

### Post by Mr. C. on 2007-06-08
From a command terminal:

```
sudo cat /proc/cpuinfo   
```

MrC

---

### Post by kalpik on 2007-06-08
Its 32 bit.. i686 is 32 bit.. x86_64 is 64 bits..

---

