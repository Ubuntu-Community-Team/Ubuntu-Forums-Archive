---
title: "I need help defeating root password for ubuntu"
date: 2007-11-08
forum: General Help
---

### Post by darksoul359 on 2007-11-08
I lost my root pass can someone help me in defeating or over ride it

---

### Post by taurus on 2007-11-08
Boot into recovery mode from GRUB menu and change to something you can remember.

```
passwd
```

---

### Post by pointone on 2007-11-08
*EDIT*

Beat me to it! ^_^

---

### Post by darksoul359 on 2007-11-09
ok so that will not work because I need the root pass to get into recovery mode so I need a different way.  I am new to Linux in fact this is the first time I have ever used it I am trying to teach my self all the treks because I hate windows with a passion I gave myself a low level user name so that i could not **** up my computer then I went and lost my password list so I cant do anything to like re download synaptic program manage and with out that I will have to reinstall Ubuntu and loose all files because I have not had the time to back them up so right now my hard drive is my life I do not want to start all over again  please help me

---

### Post by aysiu on 2007-11-09
You're not really supposed to have a root password in Ubuntu.

Maybe you can use a live CD to mount your partition and edit the /etc/shadow file to [give your root account a blank password?](http://ubuntuforums.org/showthread.php?t=513820)

---

