---
title: "got c:ss up and runnning but mouse accseleration is driving me crazy"
date: 2007-02-17
forum: General Help
---

### Post by Napster69 on 2007-02-17
so i got c:ss up and running but mouse acceleration is driving me crazy how i just dsable mouse acceleration because its driving me mad

the mouse acceleration in ubuntu i want to disable

---

### Post by fusiachi on 2007-02-17
Not sure if this is what you're looking for, but

**System>Preferences>Mouse**

Move to the "motion" tab and do as you will.

---

### Post by Napster69 on 2007-02-17
yer i no that but you cant turn it off from there how do i just disable mouse acceleration all together ?

---

### Post by fusiachi on 2007-02-17
Well, I'm not a CS player, but the internet seems to suggest that adding ```
**-noforcemaccel**
``` as a parameter in the launch options might do the trick.

---

### Post by Napster69 on 2007-02-17
hmm but is that a css option or does it do it for the system i will try now brb

---

### Post by fusiachi on 2007-02-17
That'd be exclusively for CS.  Let me know if it works.

---

### Post by Napster69 on 2007-02-17
nope dosent work all i want to no is how to just disable mouse acceleration threw ubuntu because theres no option for it in system > preferences > mouse

---

### Post by fusiachi on 2007-02-17
Again, with the caveat that I'm no guru:

```
**xset m 0 0**
```
in a terminal should do the trick.

For more info, ```
**man xset**
```

---

### Post by Napster69 on 2007-02-17
ta m8 that worked a absolute treat now to to get vetrillo and sort out the performance drop in wine  
any ideas ?

---

### Post by fusiachi on 2007-02-17
Glad to hear that's sorted.

As to Wine, I've no clue.  Haven't buggered around with it just yet.  Best of luck.

---

