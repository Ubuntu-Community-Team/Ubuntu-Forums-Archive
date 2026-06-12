---
title: "How to increase Ubuntu performance?"
date: 2015-01-16
forum: General Help
---

### Post by kenny18 on 2015-01-16
I know on windows you can increase performance by lowering graphics, and also turning on high performance mode..

Does Ubuntu have a feature like that and where can I find it?

Thanks in advance 
-Kenny

---

### Post by nerdtron on 2015-01-16
What is the specs of your computer? You can have better performance on version with a more lightweight desktop environment like Xubuntu or Lubuntu.

---

### Post by trag on 2015-01-20
Better desktop performance
[FONT=Roboto Slab]sudo apt-get install ulatency ulatencyd

[/FONT]

---

### Post by kerry_s on 2015-01-20
> **trag said:**
> Better desktop performance
[FONT=Roboto Slab]sudo apt-get install ulatency ulatencyd

[/FONT]

WARNING!! do not install, causes kernel panic, then your stuck in a boot loop. i had to reboot a lot trying to get into rescue mode, from there went to root, mounted the drive rw & removed those packages, then it was finally able to boot to desktop. not funny !!!

---

### Post by kerry_s on 2015-01-20
here some standard tips:
[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

---

