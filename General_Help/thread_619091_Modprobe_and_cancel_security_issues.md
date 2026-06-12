---
title: "Modprobe and cancel security issues"
date: 2007-11-21
forum: General Help
---

### Post by dror_trieman on 2007-11-21
Hi all :)
I have two main question, thanks for helping me:

1. I have wireless network card, and I'm using ndiswrapper. 
Each time I restart the computer, I have to modprobe the ndiswrapper again.
How I 'paste' the ndiswrapper to the linux kernel so I wouldn't have to modprobe each startup?

2. I have windows partitions (NTFS), and each restart the linux, when I access these partitions on the first time, the UBUNTU asks for the sudo password. How I remove this demand?

Thanks all and have a good day :KS

---

### Post by dror_trieman on 2007-11-26
Anybody? :confused:

---

### Post by wooster on 2007-11-26
To solve the problem about ndiswrapper module not loading at boot, type ndiswrapper in /etc/modules on a line of its own..

```
sudo gedit /etc/modules
```

---

### Post by dror_trieman on 2007-11-26
thanks man.

---

