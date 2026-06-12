---
title: "Ubuntu Server root login"
date: 2006-12-03
forum: General Help
---

### Post by gpb on 2006-12-03
I'm running Ubuntu server 6 and needed to know if there was any way of logging into the Ubuntu server as root, since I am running the server with the 'sudo' command. During the installation of Ubuntu server it does not allow me to create a root password. Any ideas????

Thanx

gpb

---

### Post by Joshua Hesketh on 2006-12-03
I believe the following will allow you to use the root account:
```

sudo passwd root

```
and follow the prompts

---

### Post by Threbus5 on 2006-12-03
This is a good thread on root login -> 
[http://ubuntuforums.org/showthread.php?t=297917&highlight=root+login](http://ubuntuforums.org/showthread.php?t=297917&highlight=root+login)

The result seems to be that sudo provides root privileges and should suffice but that if you really want to, you may set a root password from account administration.

Take care,

John

---

### Post by aysiu on 2006-12-03
I think you could just do ```
sudo -i
``` and have a root login.

---

