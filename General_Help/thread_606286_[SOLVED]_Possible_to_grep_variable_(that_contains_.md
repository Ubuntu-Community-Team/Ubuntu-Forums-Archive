---
title: "[SOLVED] Possible to grep variable (that contains a string with spaces)?"
date: 2007-11-07
forum: General Help
---

### Post by Interestedinthepenguin on 2007-11-07
I've put the the output of this:
```

tail -4 ~/.emerald/theme/theme.ini | head -1

```
(which is ```

description=Based on the AXONKOLOR VS by uac marine

```) into a variable, and have tried to use it (the variable) as my pattern for grep, but am having no luck.  I even tried adding quotes to it in different ways to keep the string together!:mad:

Anyone have any pointers?

I've searched around, but, none of the answers solved my problem.

Thanks

---

### Post by kast on 2007-11-07
VAR1=$(tail -4 ~/.emerald/theme/theme.ini | head -1)

---

### Post by Interestedinthepenguin on 2007-11-08
Man, if you asked if I'd tried that, I would've said "yes".  

I've been at this for a day and a half, with bash tutorials!  ...I don't know what I was messing up.

A million thanks.:)

---

### Post by kast on 2007-11-08
Anytime. Happy Scripting!

---

