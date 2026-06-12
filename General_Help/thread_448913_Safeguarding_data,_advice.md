---
title: "Safeguarding data, advice?"
date: 2007-05-19
forum: General Help
---

### Post by tinker123 on 2007-05-19
Hi;

I'm on Ubunut 6.10.

I've been using linux for 7 years, I want to keep more of my personal, financial information in electronic form so I think now is the time to begin administering my home system in a smarter way.

I've heard that the first thing to do when protecting your data is to set up your system so that your data is on a separate partition on your hard disk.

I have everything under /home.    I'm guessing all I need to do is to repartition my system and set up /home on its own partition.

My questions are

- 1. what is the easiest way to repartition my drive
- 2. any rules, advice about what percentage to give to data vs software/OS ?
- 3. how will my apps know to find my /home on the alternate partition
- 4. I take I will need to alter fstab to mount my data partition on start up?

Any clear, simple guides to do all of these things?   I'm not a linux geek just a desk top /end user.

Thanks much in advance

---

### Post by pjman on 2007-05-20
> **tinker123 said:**
> Hi;
- 1. what is the easiest way to repartition my drive
- 2. any rules, advice about what percentage to give to data vs software/OS ?
- 3. how will my apps know to find my /home on the alternate partition
- 4. I take I will need to alter fstab to mount my data partition on start up?


Sorry, I can only help with #1 above. I'd use [GParted]("http://gparted.sourceforge.net/"). They have a nifty LiveCd also.

I'm not sure what you mean by safeguarding your data. If you are looking at keeping your data from "prying eyes", [TrueCypt ]("http://www.truecrypt.org/")is a nice piece of software.

I hope this helps.

---

### Post by Woodgar on 2007-05-20
Long ago I needed to do the same thing myself and found this excellent guide ....

[http://www-128.ibm.com/developerworks/linux/library/l-partplan.html](http://www-128.ibm.com/developerworks/linux/library/l-partplan.html)

The guide takes you through creating and formatting a new partition, moving all of the data across and then editing fstab so that everything works properly.

Good luck !

---

