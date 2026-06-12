---
title: "Leaning the Command lines"
date: 2006-12-30
forum: General Help
---

### Post by ronbrooks on 2006-12-30
I am trying to lean the command lines and I am using this [http://www.linuxcommand.org/wss0020.php](http://www.linuxcommand.org/wss0020.php) web site to lean.  On this page they want me to bring up a file .bash_profile and edit it but I can't fine that file on my computer. Does anyone know were it is located. I am using Ubuntu 6.10.

Could someone help me find this file so I can continue with the lessons. 

Thank You

---

### Post by meng on 2006-12-30
Files beginning with . are hidden. You need to
ls -a
or
ls .*
to see them.
(It should be in your home directory)

---

### Post by ronbrooks on 2006-12-30
OK thank you meng I am new to Linux and am trying to lean as much as I can.  I think the command line is the place to start.  

Have a happy new year

---

### Post by TheWizzard on 2006-12-30
```
nano ~/.bash_profile
```

---

### Post by Doug11 on 2006-12-30
> **meng said:**
> Files beginning with . are hidden. You need to
ls -a
or
ls .*
to see them.
(It should be in your home directory)

Cool,, that is something I never knew. It pays just to do some reading.

---

