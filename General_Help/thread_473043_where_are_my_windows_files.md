---
title: "where are my windows files?"
date: 2007-06-13
forum: General Help
---

### Post by alibaba on 2007-06-13
Hello everyone :D

I had installed ubuntu before and had the two partitions right on my desktop hda1 and hda2 already, but I can't find them in Kubuntu, any help please thanks

---

### Post by dominator22 on 2007-06-13
That probably means your windows partitions aren't mounted.  Mount your partitions and see if they appear on your desktop.  If so, ensure those partitions are auto mounted in your /etc/fstab

---

### Post by alibaba on 2007-06-13
alright, how do I go about mounting them? sorry if there are 10,000 topics already on this

---

### Post by dominator22 on 2007-06-13
mount /mnt/hda1
mount /mnt/hda2

---

### Post by alibaba on 2007-06-13
tried i get this

ramzi@Alibaba:~$ mount /mnt/hda1
mount: can't find /mnt/hda1 in /etc/fstab or /etc/mtab
ramzi@Alibaba:~$ mount /mnt/hda2
mount: can't find /mnt/hda2 in /etc/fstab or /etc/mtab
ramzi@Alibaba:~$

---

### Post by alibaba on 2007-06-13
I got it now i followed

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

Thanks though

---

### Post by dominator22 on 2007-06-13
At your present level of Linux knowledge, you should consider using the [Absolute Beginner Talk](http://ubuntuforums.org/forumdisplay.php?f=73) forum.

---

