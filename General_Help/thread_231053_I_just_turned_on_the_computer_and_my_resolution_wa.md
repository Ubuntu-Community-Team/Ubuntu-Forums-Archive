---
title: "I just turned on the computer and my resolution was wrong!"
date: 2006-08-06
forum: General Help
---

### Post by TheRingmaster on 2006-08-06
can anyone tell me why my resolution got lowered down to the biggest setting and it won't let me change it back. All I did was turn on the computer.

please help

---

### Post by catlett on 2006-08-06
It shouldn't have unless you changed drivers. Use this command to reconfigure the res or use the second command to reconfig the entire x setup
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by TheRingmaster on 2006-08-06
nevermind now

I was forced to reinstall regular ubuntu

---

### Post by SigmaX on 2006-08-06
> **jpazindustries said:**
> I was forced to reinstall regular ubuntu

Just out of curiosity -- what's non-regular Ubuntu?

SigmaX

---

### Post by TheRingmaster on 2006-08-07
> **SigmaX said:**
> Just out of curiosity -- what's non-regular Ubuntu?

SigmaX
I meant that the problem was with kubuntu (I always have problems with kubuntu) so I was forced to reinstall ubuntu.

---

