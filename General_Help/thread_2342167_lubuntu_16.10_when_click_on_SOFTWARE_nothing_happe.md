---
title: "lubuntu 16.10 when click on SOFTWARE nothing happen"
date: 2016-11-04
forum: General Help
---

### Post by matteoraggi on 2016-11-04
All we know that lubuntu has an icon named SOFTWARe, where we can choose which fotware install and which uninstall, but when I do it on my lubuntu 16.10 nothing happen.
I tryed also to follow these steps:
```
sudo apt-get update
sudo apt-get remove software-center
sudo apt-get install software-center
```
I just would like to install skype, the laptop is: Acer Aspire 5670 series, model no. ZB1.

---

### Post by oldos2er on 2016-11-04
Did you try ```
sudo apt update; sudo apt install skype
``` ?

---

### Post by matteoraggi on 2016-11-04
Thanks! It works well!

---

