---
title: "How to log in as root"
date: 2008-05-01
forum: General Help
---

### Post by GoranI on 2008-05-01
I want to know how can I log into Ubuntu Hardy heron as root, because sudo command don`t fix my problem - I want to update AVG free antivirus, but it asks for root password or to be logged like root.

---

### Post by awacs on 2008-05-01
You have to set root's password:
sudo passwd root
then you can log in.

---

### Post by sisco311 on 2008-05-01
You don't need to setup a root password.
Just add your user to the avg group:
```
sudo usermod -a -G avg *your-username*
```

Or read post 5# [from:http://ubuntuforums.org/showthread.php?t=443488]("http://ubuntuforums.org/showthread.php?t=443488")

---

### Post by GoranI on 2008-05-01
> **sisco311 said:**
> You don't need to setup a root password.
Just add your user to the avg group:
```
sudo usermod -a -G avg *your-username*
```

Or read post 5# [from:http://ubuntuforums.org/showthread.php?t=443488]("http://ubuntuforums.org/showthread.php?t=443488")

I still can`t update AVG, it says "you don`t have permission to execute avgupdate":(

---

### Post by vmalep on 2008-05-01
And what about this?
```
sudo su -
```

---

### Post by sisco311 on 2008-05-01
> **GoranI said:**
> I still can`t update AVG, it says "you don`t have permission to execute avgupdate":(

Did you log out and log in or reboot the computer?

---

### Post by ilrudie on 2008-05-01
```
sudo bash
```

---

