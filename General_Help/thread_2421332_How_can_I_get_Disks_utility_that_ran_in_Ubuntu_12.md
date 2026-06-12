---
title: "How can I get Disks utility that ran in Ubuntu 12?"
date: 2019-06-19
forum: General Help
---

### Post by dora5 on 2019-06-19
We use a version of the Ubuntu Disks utility, that was just part of the basic software in Ubuntu 12.04.   Instead of telling you a drive was OK and had so many errors, it told you detailed smart drive information if you clicked on smart drive, and it would also do a fast format and take care of any partitions, unmounting, and the rest of it, all at once, in a single step, and quickly.  

The new version doesn't seem to have any option to display smart data at all, it will only format partitions, not just the drive as a whole, and it takes forever to do a format, in other words, it doesn't do a quick format.

How can I get the old version?   

Is there a way to get it from Ubuntu 12 and recompile it or something?

We do NOT want to use other software that does SOME of the same things differently.   

Right now we're using Ubuntu 12 because it runs the version of Disks we want, and it would be useful to be able to use Ubuntu 18.   

Thanks!

Yours,
Dora Smith

---

### Post by deadflowr on 2019-06-19
The settings you want are in that hamburger (three horizontal lines) icon in the top panel area on the right side.
That has smart and disk format options.

---

### Post by dora5 on 2019-06-20
You're right, it is!  I tested it.  Thanks!   That's completely unintuitive, though, and in online discussions everyone who seems to actually observe smart data uses Ubuntu 12

---

### Post by dora5 on 2019-06-20
One thing, though.  Which value is the Current pending sector count?  We need to see if that value is not 0.   If you don't specifically look at it, all it tells you is that there  are a few bad sectors - same thing it tells you if there are 1,218,316 bad sectors and the threshhold is 5.   

Thanks!

---

### Post by deadflowr on 2019-06-20
Not sure what you mean?
Values should be self evident in the smart data popup window.

---

### Post by CatKiller on 2019-06-20
> **dora5 said:**
> in online discussions everyone who seems to actually observe smart data uses Ubuntu 12
Ubuntu 12.04 has been unsupported for over two years. No one should be using it.

---

