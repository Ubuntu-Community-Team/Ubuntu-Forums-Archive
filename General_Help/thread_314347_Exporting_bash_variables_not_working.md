---
title: "Exporting bash variables not working"
date: 2006-12-07
forum: General Help
---

### Post by dmarkey on 2006-12-07
ok for example

name="DAVID"
export name


now when i goto another shell name is unset
this is driving me crazy, can anyone help?

---

### Post by taurus on 2006-12-07
Where did you add those two commands?

---

### Post by dmarkey on 2006-12-07
i just manually put them into a terminal

---

### Post by taurus on 2006-12-07
Then "name" is only available for that terminal, the one that you added from a command line!  If you want it to available everytime you open a terminal, then you need to add those two lines in your ~/.bashrc.

---

### Post by dmarkey on 2006-12-07
no, when you export a variable it should be then available globally

---

### Post by Tomosaur on 2006-12-07
> **dmarkey said:**
> no, when you export a variable it should be then available globally

The only way to set a permanent variable in Ubuntu is to define it in ~/.bashrc. This is default behaviour. You may be able to change it, but I personally don't know how you'd do that, and I prefer the .bashrc method anyway.

---

### Post by dmarkey on 2006-12-07
When we "export" an environment variable under bash, any subsequent program that we run can read our setting, whether it is a shell script or not.
thats from 
[http://www-128.ibm.com/developerworks/library/l-bash.html](http://www-128.ibm.com/developerworks/library/l-bash.html)

export is standard bash stuff.

---

