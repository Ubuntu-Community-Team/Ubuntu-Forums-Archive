---
title: "sudo: effective uid is not 0, is sudo installed setuid root?"
date: 2013-02-01
forum: General Help
---

### Post by TipTricky on 2013-02-01
Well i made a mistake haha. I was typing sudo chmod -R 777 www when i made the mistake of prematurely hitting enter and now when i type a sudo command i get that error. Im assuming its because i managed to change the owner of usr from root to my user and i here that is not very good at all. Any way to fix without fresh install???

---

### Post by Impavidus on 2013-02-01
If you typed```
sudo chmod -R 777 www
``` you have given everyone full permissions in the www directory. You didn't change ownership of anything nor delete anything or set anything as non-executable. It may be a security risk though. Are you sure this is what caused your problem?

---

### Post by TipTricky on 2013-02-02
Haha what i typed was more like ```
sudo chmod -R 777 /
```

Unintentionally i know that command is a terrible idea and i know the security risk. But yeah thats whats causing the problem.

---

### Post by rnerwein on 2013-02-02
> **TipTricky said:**
> Haha what i typed was more like ```
sudo chmod -R 777 /
```Unintentionally i know that command is a terrible idea and i know the security risk. But yeah thats whats causing the problem.
hi trpTricky
sorry when i have to tell you: your are the loser. reinstall your system.
do you heard about: [sorcerer's]("http://dict.leo.org/ende?lp=ende&p=DOKJAA&search=sorcerer%27s&trestr=0x8001") [apprentice]("http://dict.leo.org/ende?lp=ende&p=DOKJAA&search=apprentice&trestr=0x8001")
ciao

---

