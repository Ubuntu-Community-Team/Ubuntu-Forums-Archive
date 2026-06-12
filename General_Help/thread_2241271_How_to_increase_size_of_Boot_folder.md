---
title: "How to increase size of Boot folder"
date: 2014-08-25
forum: General Help
---

### Post by janda29 on 2014-08-25
I have just solved a low disk problem with help from this forum.  How do I increase the size of the Boot folder and should I do so in the first place?It now shows some 20.7 Mb free.  Using 14.04 LTS

---

### Post by Impavidus on 2014-08-25
Best is to prevent old stuff from accumulating there in the first place. You can autoremove old packages when you've installed a new kernel.```
sudo apt-get --purge autoremove
```or use the GUI.

---

### Post by grahammechanical on 2014-08-25
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Elfy on 2014-08-25
I could be wrong here - but I suspect the rest of the file system is LVM, so you'd want to be looking at how to reduce that - then you should have space to increase /boot.

The other option is to take this as a learning opportunity and to make sure to keep an eye on the kernels you have installed and remove old ones, so that you don't get the same issue again ;)

---

