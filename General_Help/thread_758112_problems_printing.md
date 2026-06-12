---
title: "problems printing"
date: 2008-04-17
forum: General Help
---

### Post by rogic on 2008-04-17
Hi,

I did the upgrade from 7.04 to 7.10 and now I cannot print anymore. To be more specific, I can print some easy stuff like a printer's test page or a text file but anything that is a bit more complicated, with pictures for example, takes for ever to print (the either prints out one page every 10 min or reports insufficient memory and cancels the job). My printer is HP Color LaserJet 4500 and I am using v2014.200 Postscript driver. My colleague has the exact same settings as me and he can print fine. 
I did try to disable App Armour but it didn't help.
Another problem that I am having now is that my Firefox keeps freezing with the new version.
All was working fine before the upgrade.

Please advise!

Thanks in advance,
Sanja

---

### Post by northern lights on 2008-04-17
What are you're system's specs? Especially, how much physical memory / RAM do you have?

Apart from the printing job reporting exactly that being insufficient, the firefox issue points to the same.

It doesn't freeze completely, does it? Only for a few seconds, or so? That would point to memory issues, anyways. Does it happen with several tabs more frequently than with one or two? Would point to the same.

---

### Post by rogic on 2008-04-17
I have 4Gb. But the insufficient memory message is coming from the  printer which has 64 Mb.
The firefox behaves as you explained but I don't think it depends on the number of tabs open; it freezes also when I have only 1 or 2 tabs open.

Sanja

---

### Post by northern lights on 2008-04-17
Darn. I'm dumbfounded. Can you post the output of```
free -m
```and```
dmesg
```right after firefox unfreezing? Thank you.

---

### Post by rogic on 2008-04-17
Here is the memory thing:                 

                   total       used       free     shared    buffers     cached
Mem:          3892       3835         57          0        205       2331
-/+ buffers/cache:       1298       2593
Swap:         1906         29       1876

It seems that it has very little free memory. The other command gives a huge output, anything specific that you are looking for?

Thanks for your help,
sanja

---

