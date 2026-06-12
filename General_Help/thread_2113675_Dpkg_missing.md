---
title: "Dpkg missing"
date: 2013-02-08
forum: General Help
---

### Post by Tarkers on 2013-02-08
I've somehow mucked up dpkg, the dpkg file itself doesn't seem to exist even though I have some of the other dkpg files.

I'm not quite sure how to restore it so it functions properly again, I'm fairly new and could use some advice.

---

### Post by fantab on 2013-02-08
Tarkers, we need more info than what you have provided. 

Tell us how do you know you have "mucked up dpkg" and also tell us what you were doing for us to be able to help you.

You can also post the output of "sudo apt-get update" to get started.

Meanwhile try this from terminal:

```
sudo dpkg --configure -a
```

... and post the output if it doesn't help.

---

