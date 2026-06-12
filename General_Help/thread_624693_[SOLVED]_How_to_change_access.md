---
title: "[SOLVED] How to change access"
date: 2007-11-27
forum: General Help
---

### Post by june_c21 on 2007-11-27
hi, i try to change the permission in filesystem but the error pop up said i don't have permission. i'm the administrator but why i change it ?

---

### Post by taurus on 2007-11-27
What filesystem is that?  And what directory (or mount point) do you try to change?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by june_c21 on 2007-11-27
i want to change the access in etc/php5

---

### Post by taurus on 2007-11-27
You mean you want to be able to modify files in /etc/php5?  You need to use sudo/gksudo.  Changing permissions just because you don't feel like using sudo is not a good solution.  In fact, it would break your machine if you don't know what you are doing with the permissions.  

So, exactly what you want to do to /etc/php5?

---

### Post by june_c21 on 2007-11-27
sorry, i'm new in ubuntu. i want to change some stuffs in the config file. so how to write the command?

---

### Post by taurus on 2007-11-27
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/php5/**filename**
```
Replace **filename** with the actual name of the file that you need to modify.

---

