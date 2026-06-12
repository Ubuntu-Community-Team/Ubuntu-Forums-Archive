---
title: "Get Grub to recognize my hard drive"
date: 2008-05-08
forum: General Help
---

### Post by ZeldaFan on 2008-05-08
I have two internal hard drives in my laptop. One that has ubuntu on it (and has the grub installed to it as well) and one that has vista on it. I installed ubuntu on my first hard drive with only that HDD in it, so the vista HDD is in no way related to my ubuntu installation. However, since my laptop supports two HDD's, I put my vista HDD in the second slot. How do I get grub to recognize my vista OS on the second HDD so I can boot into it?

---

### Post by hermes0710 on 2008-05-09
First you have to know in which partition of your second drive is vista installed. Once you know that, you just have to manually enter an entry in /boot/grub/menu.lst pointing to vista:

title Microsoft Windows Vista
root (hd1,0)
savedefault
makeactive
chainloader +1

---

### Post by ZeldaFan on 2008-05-09
Sorry if the answer is obvious, but how do I determine what partition my vista install is on? I know for a fact that it completely occupied my second hard drive and the partitioning was automatically done by the Vista installer.

---

### Post by ZeldaFan on 2008-05-09
Ok, I installed GParted actually and just navigated to the partition that had my vista install on it. It says the path is: /dev/sdb1
Is that what I am looking for?

---

### Post by mc4man on 2008-05-09
try what hermes0710 suggested
root (hd1,0)
hd1 = hdd 2  (sdb)
0 =  partition 1

---

### Post by ZeldaFan on 2008-05-09
Thanks so much guys, that did the trick. Now I can dual boot without ever really partitioning my laptop with two OS's.

---

