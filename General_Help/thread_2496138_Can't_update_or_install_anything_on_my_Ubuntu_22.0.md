---
title: "Can't update or install anything on my Ubuntu 22.04 machine"
date: 2024-03-15
forum: General Help
---

### Post by runtime989 on 2024-03-15
HELLO THERE!
I am using  Ubuntu 22.04 and recently i installed Genymotion on my machine.For few days my PC was working f9 but from last few days i am getting many errors.I can't open my terminal from the softwares,i have to go to a folder and open terminal there.Now when I use sudo apt update,i get many errors like:

   Traceback (most recent call last):  File "/usr/lib/cnf-update-db", line 3, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code


I searched the  internet and i think it may be the problem with python.
puthon version is 3.10.12

please help @everyone 
it is driving me crazy

---

### Post by 14nd on 2024-03-15
pls pls tell us you have a system restore...(timeshift) ?

---

### Post by runtime989 on 2024-03-15
No i don't have??

---

