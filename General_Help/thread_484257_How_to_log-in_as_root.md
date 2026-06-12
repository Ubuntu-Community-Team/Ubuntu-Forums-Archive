---
title: "How to log-in as root ?"
date: 2007-06-25
forum: General Help
---

### Post by GoranI on 2007-06-25
How to login as root, but not in terminal, is it possible to login on some other way ?

---

### Post by init1 on 2007-06-25
sudo passwd root
(type in your user password, and then your desired root password)
then when the login asks for username, say
root
and then give your password.

---

### Post by GoranI on 2007-06-25
I tried this, but it says "System administrator can`t login in this screen" (login screen).

---

### Post by TheFoe92 on 2007-06-25
Or, if you don't want to fiddle with Terminal, you can go to System > Administration > Users and Groups. Then click 'root' and click 'Properties'. Under 'Password' make sure 'Set password by hand' is chosen, then type in a password for root. Click OK, logout and login as 'root' with the password you just typed in. Be careful when signed in as root : they have unlimited power over the system and if you delete or alter any system file you can make your system unstable.

---

### Post by H.E. Pennypacker on 2007-06-25
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

---

### Post by TheFoe92 on 2007-06-25
> **GoranI said:**
> I tried this, but it says "System administrator can`t login in this screen" (login screen).

Go to System > Administration > Login Window. Click the 'Security' tab then check the 'Allow local system administrator login' box. Click OK, and follow the steps above.

---

### Post by rillip on 2007-06-25
The above by TheFoe92 should definitely work, but understand this is not recommended.

---

