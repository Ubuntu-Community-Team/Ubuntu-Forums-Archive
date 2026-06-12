---
title: "How can I list all my sata drives?"
date: 2007-07-10
forum: General Help
---

### Post by glave on 2007-07-10
When I want to find out information about my drives (ide), I can normally go to /proc/ide and check it out. I have 2 promise sata raid cards, and I cannot find a way to replicate this type of info.

I have 10 sata drives total in the machine, and would like to be able to check out things like what drives do I have (sda, sdb, etc), what their model is, etc. I know this stuff fairly well when I have to do maintenance, but when things run smoothly for a while, you tend to forget what was in there when its time to work on it again.

Is there any easy eay to list this info? Even the most basic ability to see what drives I have (sda, sdb, etc) would be helpful.

---

### Post by futz on 2007-07-10
Seems too easy, but... 
```
sudo fdisk -l
```

---

### Post by glave on 2007-07-10
Actually that does list out the devices perfectly...

Now if I can discern info on the drives like MODEL and such, that would be great.

---

### Post by glave on 2007-07-10
I just installed SMART and while gathering data on the drives, I noticed that it will indeed report to me the model number.

---

