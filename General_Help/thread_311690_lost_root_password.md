---
title: "lost root password"
date: 2006-12-03
forum: General Help
---

### Post by Shai Gar on 2006-12-03
need to log into root in order to use alien (and install limewire), but i typed in "su" and then "97585803"* but i recieved this

[B]shaigar@shaigar:~$ su
Password:
su: Authentication failure
Sorry.[/B]

I was certain that I saved my root password as that, and now I'm ******. Is there a way that I can solve this problem short of reinstalling dapper drake?




*not my real root password

---

### Post by ato on 2006-12-03
Ubuntu does'n have a real root password.
You must use sudo with your user password.
Or you can set a root password typing:
```
sudo passwd
```

---

### Post by ayoli on 2006-12-03
root account is disabled by default on ubuntu, enable it is a bad idea. you should use sudo instaed.
if you want to be logged as root in a console type in:
```
sudo -i
```
you 'll be prompted for your **user** password, and then you will grant root privileges.

---

### Post by lamego on 2006-12-03
The safe way to do what you need is:
```
sudo alien file.rpm
```

Also, by you question you are quite new to Ubuntu, you should avoid using .rpms .

---

### Post by taurus on 2006-12-03
You need to read this.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by steve.horsley on 2006-12-03
**sudo su** will give you a root prompt. No logging in required.

I would ask why you want to use alien. Most packages you might want are already in the Ubuntu repositories. Have you checked Synaptic Package Manager first?

---

