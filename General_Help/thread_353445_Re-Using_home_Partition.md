---
title: "Re-Using /home Partition"
date: 2007-02-04
forum: General Help
---

### Post by CREEPING DEATH on 2007-02-04
OK, last night I tried to upgrade from 6.06.1 LTS to 6/10.  It did not go well, after messing with it for a couple of hours (recovery CD), I still don't have sound.
Anyway, I want to try out Feisty.  I've downloaded both the Desktop CD and Alternate CD.  I'd like to install it and re-use the current /home partition.  How do I do this properly?

Thanks,
CD

---

### Post by jimbren on 2007-02-04
Re-using /home is easy.  When you get to the partitioning section, you don't select guided partitioning, and you just don't format that partition.  On the next screen you get to select the labels, and you'll want to label that partition as /home.  

If you can do a back up prior, that's the safest thing to do--that way even if you muck things up or just decide for some reason to format everything, you can then just restore everything from your backup.

Try it, you'll like it.

---

### Post by meng on 2007-02-04
As jimbren said, the important thing is that when it comes to manual partitioning, select the option "keep existing data" and also specify the mountpoint as "/home"

---

### Post by CREEPING DEATH on 2007-02-05
Is it better to use the alternate or desktop CD?  I have both, I want this wounded machine 100% again.  Do I just enter in the same user name and password?

Thanks,
CD

---

### Post by meng on 2007-02-05
I vote for Alternate - quicker. Yes just use same username and password as before.

---

### Post by CREEPING DEATH on 2007-02-05
Thank you!!!

CD

---

### Post by CREEPING DEATH on 2007-02-05
OK I installed it, and it's working great!  Nothing lost, everything seems to work so far!
I love Linux!

CD

---

