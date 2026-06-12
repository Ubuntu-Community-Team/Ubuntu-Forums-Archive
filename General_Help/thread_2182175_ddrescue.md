---
title: "ddrescue"
date: 2013-10-20
forum: General Help
---

### Post by alessandroar on 2013-10-20
I have a broken disk with all the photos from 1t the system sees the unit but do not enter, I did a live cd SystemRescueCd, I do fdisk to identify the disk, I read the guide to make ddrescue a copy of the image in the external disk 1t, after a day of work turned empty "current rate 0" etc.., then I locked ddrescue, I now find myself on the failed disk files foto.img of 0 bytes and foto.log, it seems that I reversed in ddrescue commands for copying discs, what can 'be successful, i'm sure I gave the correct commands with the target disk toshiba .... you know help me?
thank you very much

---

### Post by alessandroar on 2013-10-21
I have a broken disk with all the photos from 1t the system sees the unit but do not enter, I did a live cd SystemRescueCd, I do fdisk to identify the disk, I read the guide to make ddrescue a copy of the image in the external disk 1t, after a day of work turned empty "current rate 0" etc.., then I locked ddrescue, I now find myself on the failed disk files foto.img of 0 bytes and foto.log, it seems that I reversed in ddrescue commands for copying discs, what can 'be successful, i'm sure I gave the correct commands with the target disk toshiba .... you know help me?
thank you very much

---

### Post by sudodus on 2013-10-21
Did you try according to the ***examples*** in this help text? ```
info ddrescue
```

I suggest you clone what can be cloned to another drive of at least the same size, and write the log file to a third drive. (Is that what you tried, or did you try to make an image file?) Please post the command that you tried to use!

-o-

Are you sure it is hardware problems? Or could it be a corrupt file system?

---

### Post by mörgæs on 2013-10-21
Please don't create multiple threads on the same problem. 
Merged.

---

### Post by alessandroar on 2013-10-22
sorry

---

### Post by alessandroar on 2013-10-22
the ezternal drive is same size 1t, I'm not sure I remember most the command. It is normal to write the img file and also log in corrupt disk?

---

### Post by jamesisin on 2013-10-22
Yes, definitely clone the bad drive and set it aside.  Work on the clone in your recovery attempts.

---

### Post by sudodus on 2013-10-22
> **jamesisin said:**
> Yes, definitely clone the bad drive and set it aside.  Work on the clone in your recovery attempts.

+1

---

### Post by alessandroar on 2013-10-23
in the bad drive there file .img size 0 kb and a .log file of 259 kb, I may have overwritten the bad drive?

---

### Post by sudodus on 2013-10-24
Please post the output of the following commands

```
sudo parted -l
sudo fdisk -lu
```
and describe in you own words which drive is the bad one (source) and the one to be the clone (target) and the one to boot from  and the one where to write the log file (maybe the same as the one to boot from).

Also describe which ddrescue command that you tried (or at least *try* to describe it).

---

### Post by jamesisin on 2013-10-27
I have an example use of dd in this article.

[http://jamesisin.com/a_high-tech_blech/index.php/2013/04/more-for-copying-drives-or-partitions/](http://jamesisin.com/a_high-tech_blech/index.php/2013/04/more-for-copying-drives-or-partitions/)

---

