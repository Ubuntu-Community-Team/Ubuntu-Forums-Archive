---
title: "Conky is eating my CPU"
date: 2007-05-30
forum: General Help
---

### Post by JMO707 on 2007-05-30
I really didnt know why things became so slow on my Fluxbox session, but take a look to this:


Mmm, just when he started to like me =/

---

### Post by taurus on 2007-05-30
Can you post your ~/.conkyrc?

```
cat ~/.conkyrc
```

---

### Post by reclusivemonkey on 2007-05-30
It could be your fortune... I know in the conky help files it says that exec'ing isn't too clever. I don't have a problem with it doing remind for me, but I know here at work when I pull a fortune via cygwin on my USB drive it sometimes takes an age. Try removing the fortune, and see if that helps. If it does, you could change it to read a fortune from a text file, and then run a cronjob to output a fortune to this text file every hour, or however frequently you want to know your fortune ;-)

---

### Post by JMO707 on 2007-05-30
Wow, in effect, it was *Fortune*.

To the ones with this problem:

[QUOTE=reclusivemonkey]It could be your fortune... I know in the conky help files it says that exec'ing isn't too clever[/QUOTE]

Thanks!

---

