---
title: "2 questions"
date: 2008-01-09
forum: General Help
---

### Post by cheaptrick on 2008-01-09
1.I have installed xubuntu on top of ubuntu, i did quite like xfce environment, i want to run a pure xubuntu, so how do i delete the gnome-ubuntu? 

2.i have installed linux mint on another partition, Didnt quite like it,  i want to format that partition. However i did notice the boot up is using the grub and menu.lst from that linux mint partition, so if i format that partition, will i be able to boot up normally?

---

### Post by dlegend on 2008-01-09
1. sudo apt-get remove gnome-desktop
2. not sure

---

### Post by -grubby on 2008-01-10
1: sudo apt-get remove ubuntu-desktop
2: well you will have to redo the grub boot sector using the ubuntu live-CD (I don't know how , I've never had to) if you want to format that partition (if you format it you will remove the boot sector and you will have to run it from your other partition)

---

### Post by cheaptrick on 2008-01-11
hmm is there an easier way to redo the grub bootsector?

---

### Post by jken146 on 2008-01-11
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

