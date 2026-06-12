---
title: "creating new account from tty"
date: 2007-03-04
forum: General Help
---

### Post by nickoli_02 on 2007-03-04
So, I've done a reinstall of ubuntu and somehow skipped the step where it creates a user account for you. How can I create a new user under the admin group from the recovery mode tty?

---

### Post by lotu on 2007-03-04
useradd <username> -G <group,names>
passwd <username>       to set the password
in this case you want the admin  and sudo group. So do something like this
useradd jhon -G  admin,sudo
passwd jhon
then enter the password and you should be able to log in as your new user
if  you are still having trouble read.  
man useradd
man passwd
man adduser

---

### Post by nickoli_02 on 2007-03-05
thanks :)

---

