---
title: "How do I Acess a NTFS Slave drive"
date: 2008-06-12
forum: General Help
---

### Post by morbidxbean on 2008-06-12
ok     I just switched from windows to linux today... when I had used windows I had a 160gb slave drive to store extra stuff off and a 40gb to store the OS and programs on.....I installed Ubuntu on the 40gb and its running like a charm....but when I want to access them files on that 160gb I will get some error about not able to access...i asumed it was something related to NTFS...Am i wrong? How can i access it.

---

### Post by tamoneya on 2008-06-12
post the output of the following command in terminal:```
sudo fdisk -l
```

---

### Post by drs305 on 2008-06-12
Earlier today we discussed NTFS partitions and how to mount them in this thread:
[http://ubuntuforums.org/showthread.php?t=827434]("http://ubuntuforums.org/showthread.php?t=827434")

It should give you what you need.

---

### Post by Joeb454 on 2008-06-12
If you want to Auto-Mount it every time you boot, you can try the link at the bottom of my sig, it's worked every time for me :)

Though if not, drs305's thread may be a better choice :)

---

### Post by drs305 on 2008-06-12
> **Joeb454 said:**
> If you want to Auto-Mount it every time you boot, you can try the link at the bottom of my sig, it's worked every time for me :)

Though if not, drs305's thread may be a better choice :)

The thread I was involved in is not nearly as concise. I'd use yours and only go to the other as a backup. :)

---

