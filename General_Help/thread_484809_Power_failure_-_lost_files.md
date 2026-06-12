---
title: "Power failure - lost files"
date: 2007-06-26
forum: General Help
---

### Post by denispyr on 2007-06-26
Hi all.
I had a power failure and now I cannot see any of my files.
I am running KUbuntu 7.0.4. I have a a disk partition mounted as /media/develop, filesystem jsf. After a power failure, this mount is almost empty. By "almost" I mean that the only content I see is an empty folder (it was not empty before the failure!). On the other hand, I suspect that the files are there because GPartEd and Krusader say that a good percentage of the partition is used.
Any pointers on what I should do to retrieve my files?
TIA
Denis

---

### Post by mikeypizano on 2007-06-26
Try the hard drive in a different computer that can read a Linux drive. I also sugest you get a UPS (not the shipping company, its a battery backup :-D) reprevent thi from happening again.

---

### Post by denispyr on 2007-06-26
It seems that the simple fsck I ran was enough. I tried ```
fsck.jfs -fv /dev/PARTITION
``` (thanks ludist), remount and everything i ok.
BTW thx mickey - I will surely buy UPS (the device, not the company ;) )
> **denispyr said:**
> Hi all.
I had a power failure and now I cannot see any of my files.
I am running KUbuntu 7.0.4. I have a a disk partition mounted as /media/develop, filesystem jsf. After a power failure, this mount is almost empty. By "almost" I mean that the only content I see is an empty folder (it was not empty before the failure!). On the other hand, I suspect that the files are there because GPartEd and Krusader say that a good percentage of the partition is used.
Any pointers on what I should do to retrieve my files?
TIA
Denis

---

### Post by mikeypizano on 2007-06-26
Glad ya got it to work again! I suggest an APC brand.

---

