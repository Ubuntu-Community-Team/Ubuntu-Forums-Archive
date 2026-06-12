---
title: "remove virtualbox"
date: 2007-05-20
forum: General Help
---

### Post by Cam1223 on 2007-05-20
i installed it but i guess it didnt work, when i try to open it nothing happens and i dont know how to delete it...yea i kno what a newb

---

### Post by bobplano on 2007-05-20
how did you install it? by the terminal you can just do sudo aptitude/apt-get remove ...
synaptic and add/remove you can just check it for removal. sorry if you can't get it these ways, i am just using ubuntu more and more and have no reason for a virtual machine

---

### Post by Cam1223 on 2007-05-20
i downloaded a .deb package and did a force install since im on 64 and it was a 32bit. i dont kno how to remove a program installed manually with a deb package can u guys help me out? thx for the quick reply

---

### Post by bodhi.zazen on 2007-05-22
```
sudo dpkg -r VirtualBox
```

---

