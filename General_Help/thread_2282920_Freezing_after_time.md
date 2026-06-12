---
title: "Freezing after time?"
date: 2015-06-17
forum: General Help
---

### Post by Kreuzsarg on 2015-06-17
Hello,

I am using Lubuntu since today.

First, it worked very well the first 3-4 hours. 

But now, I get random freezes without a reason. Sometime after 10 minutes, sometimes longer, the only way to get off it, is the Power-button...
It's really annoying and I don't want move back to windows..

I hope you guys can help me, if you need any information, tell me.

Regards,

Kreuz

---

### Post by ajgreeny on 2015-06-17
What hardware?

---

### Post by Kreuzsarg on 2015-06-18
I think it's not because of my hardware, because I never had it in my life with windows.

But I read somethings and they saying me about a known freeze bug with NVIDIA graphic card or a kernel?

---

### Post by tgalati4 on 2015-06-18
Welcome to the forums.

Open a terminal.  Post the output of:

```
lspci | grep VGA
```

---

### Post by Kreuzsarg on 2015-06-18
I also installed the newest driver 352..but still random freezes

04:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640] (rev a1)
Subsystem: Device 196e:093c
Kernel driver in use: nvidia

---

### Post by tgalati4 on 2015-06-18
What kernel are you running?

```
uname -a
```

Have you performed all the updates that are available?  Check your power supply in BIOS or with a volt meter.  12VDC should be 12VDC and 5VDC should be 5VDC.  Any lower values (-10%) can cause lockups.

Run *memtest* from the grub menu.  Let it go for 30 complete cycles--this will take several hours.  If it locks up before then, then you know you have a hardware problem.

---

### Post by Kreuzsarg on 2015-06-18
Already did these things, when I readed some options.. No hardware problems, everything ok with the hardware. Also updated to the newest driver, but same..I heard something that it is a nvidia bug caused after version 275.58..but I can't install 275.58 because it needs downgraded xorg or idk..

---

### Post by tgalati4 on 2015-06-18
Install an older version of Lubuntu--one that supports the 275.58 proprietary driver.

---

### Post by Kreuzsarg on 2015-06-19
After some testing, I found the problem..It's Chrome Browser what freezes my whole system, I also disabled gpu and hardware thingy for it and also updated kernel to 3.19..but still. I don't get freezes with firefox..but I need chrome to play the browsergame I play..with firefox it's just impossible to play lagfree -.-

Anyone a idea?

---

