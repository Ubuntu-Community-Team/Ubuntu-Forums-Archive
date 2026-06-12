---
title: "Prtition Editor Will Not Work"
date: 2008-01-20
forum: General Help
---

### Post by bobcat2m on 2008-01-20
HI,

I'm new to Ubuntu.  My system says the root is full.  I've tried to use partition editor (from within the Ubuntu installed on my PC and also from the INSTALL CD) it does not work.  It starts and then does not move beyond the scan part where it's looking for your drives.  It just hangs there with the indicator bar going back and forth.  This is my second post on this issue as the first post failed to generate a solution.

Any Help is Greatly Appreciated - Thank in Advance

---

### Post by eggdeng on 2008-01-20
You could try 
```
sudo shutdown -hF now
```
This will force a filesystem check on next boot.

---

