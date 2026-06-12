---
title: "[SOLVED] Removing partition label"
date: 2007-09-09
forum: General Help
---

### Post by soxs on 2007-09-09
I messed around with my home partition and I finally got 2 partitions left labeled home (not named home, not mounted @ /home only labeled home) (left click on mounted partition on the desktop, change to "volume" tab)

I got around the tool e2label which allows me to *change* the label to whatever.
I even tried to get some info about it, if it is possible to remove the label using e2label...
But google did not spit out one single usable result.
So.. my Q:

**How can I remove a partition's label?**

Btw.. does genitive require a " ' " or not? *g*

---

### Post by expatCM on 2007-09-09
thought it was simple command line syntax in the form of 

e2label path/name of drive label name

example - e2label /dev/sda5 data

Presumably if you leave the label name blank that is what will be reflected.

---

### Post by strider1551 on 2007-09-09
> Btw.. does genitive require a " ' " or not? *g*

The genitive can be shortened with an apostrophe:  "a partition's label" and "the label of a partition" are both correct.  In spoken English, people almost always use the shortened form.  If you omitted the apostrophe it would be assumed to be a typo ("a partitions label" makes no sense)

---

### Post by soxs on 2007-09-09
```
e2label /dev/sdb5 data
``` renames the label to data
```
e2label /dev/sdb5 
``` returns the partition's (thx to strider1551 :-P) label, and doesn't rename it

Edit: May be there a another tool for ext2/ext3 partition renaming for linux? Plx give me a hint!

---

### Post by thefrood on 2007-09-23
try something along the lines of

```
tune2fs -L "" /dev/sdb5
```

obviously adjusting the device path to suit your needs.

---

### Post by soxs on 2007-09-24
thx a lot, worked like a charm :grin:

---

