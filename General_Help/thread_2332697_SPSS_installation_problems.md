---
title: "SPSS installation problems"
date: 2016-08-03
forum: General Help
---

### Post by rryesuafuga on 2016-08-03
I managed to install SPSS. Then nothing happened. It did not appear under applications. Then I found that it was installed in the OPT folder. I tried reinstalling SPSS and still there was no change. I tried checking in the OPT folder for the correct file to open but I could not identify which one to open.

How should I fix this so it will appear in the application menu? Which is the correct file I should open in the OPT folder if that can work?




I use ubuntu 14.04.


Thanks!

---

### Post by howefield on 2016-08-03
Thread moved to the "*General Help*" forum.

---

### Post by gordintoronto on 2016-08-03
Where did you get SPSS from? Since it's not in the repositories, OPT is the normal place where it should be installed. If you open a terminal and type spss what happens?

---

### Post by mastablasta on 2016-08-04
what version of SPSS? what procedure was used for install? is the version 32 bit or 64 bit? what version of the OS (32bit or 64 bit)? 

@gordintoronto - SPSS is a statistical program now owned by IBM

@op - PSPP is opensource implementation. Has a bit more limited features (at least for now), but is OK for basic research (multivariable analysys and such). the most i disliked is the output tables can't really be edited. a copy into MS excel (or LO calc) could help with that, but i also experienced crashes every now and then. well its still a work in progress so i hope they make it to version 1.0

this page makes sense - it's in german but oyu cna use a translator. basically if yoour OS is 64 bit make sure you have 32 bit libraries installed. : [https://wiki.ubuntuusers.de/SPSS/](https://wiki.ubuntuusers.de/SPSS/)

---

### Post by SeijiSensei on 2016-08-04
> **gordintoronto said:**
> Where did you get SPSS from? Since it's not in the repositories, OPT is the normal place where it should be installed. If you open a terminal and type spss what happens?
I'm going to guess nothing will happen since /opt is not in the standard path.  

OP, do you see a rather large file called spss in the directory where it was installed under /opt?  Try running that from the command prompt with "/opt/path/to/spss/spss" or some such.

PSPP works well for simple analyses like frequencies and crosstabs.  I don't think it has more advanced features like discriminant or factor analysis though I haven't looked lately.

Most of [my work]("http://politicsbythenumbers.org/") consists of estimating various regression models.  For that, I use the open-source [gretl]("http://gretl.sourceforge.net/"). It's in the repositories.

---

