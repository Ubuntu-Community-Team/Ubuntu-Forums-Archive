---
title: "cant get to login screen"
date: 2007-05-23
forum: General Help
---

### Post by themadhippy on 2007-05-23
so ive some how broken fiesty,the machine boots up fine,but at the point were the login screen  should appeer all i get is a blank screen no cursor nothing.starting in recovery mode gets me to the prompt "root@hippy-desktop:~#"
tryed "start x" and same blank screen,"apt-get -f install" throws up a segmentaion fault as does "sudo apt-get install ubuntu=desktop".I would normally reinstall but theres a far bit of stuff on the machine that id rather try and keep,also my modem is a pain to  setup.Anybody help me get things back to normal

---

### Post by taurus on 2007-05-23
What is the error message when you try to start X at the prompt?

```
startx
```
Perhaps you need to reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
```

---

### Post by themadhippy on 2007-05-23
>  	What is the error message when you try to start X at the prompt?

no idea the screen goes blank almost imediatley.However the second command seems to have done the trick,ive no idea what half of the things it was asking me ,i accepted the defaults,but it worked:p
Many thanks taurus for your help

---

