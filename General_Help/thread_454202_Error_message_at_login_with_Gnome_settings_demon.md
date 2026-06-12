---
title: "Error message at login with Gnome settings demon"
date: 2007-05-25
forum: General Help
---

### Post by FizzBuntu on 2007-05-25
Hi
At login and with all users, i get an error message 
[IMG]http://macserver.servebeer.com/errorgnome.png[/IMG]

what's that all about
I'm on fesity fawn and NXServer

---

### Post by mbradlcu on 2007-05-27
I've seen this error when having a messed up /etc/hosts file, here's mine:
root@matt-x64:~# cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       matt-x64

"matt-x64" is the name of my machine as found in the /etc/hostname file:
root@matt-x64:~# cat /etc/hostname 
matt-x64

---

### Post by FizzBuntu on 2007-05-27
everything looks good here...
any other ideas ?

---

### Post by mbradlcu on 2007-05-27
I'd use the shotgun approach and create another user and try and log in as it.. at least you'd know if it's related to ~/.gnome settings.

---

### Post by dom085 on 2007-05-27
Hi

I'm very new to Ubuntu and Linux in general and I have the exact same GNOME error message after my log-in, which only results in a default desktop wallpaper- no toolbars, nothing.

Have you resolved it?

Thanks.

---

### Post by FizzBuntu on 2007-05-29
yes, ,I've resolved it (after trying the shotgun approache)
The thing is that I'm not using evolution (I'm using Mozilla), so I've uninstalled it...
That was my mistake, 'cause it seems that the gnome deamon setting somehow depends on the evolution-data-server-common or evolution-data-server.
After I've re-installed those two, everything's back to normal, got my settings and all...

miracle...

I would still like to uninstall the unused apps, but it seems that many of them are needed in the system...

good luck

---

### Post by mjitkop on 2007-05-31
I just came here because I noticed the same error message when I started my PC earlier. I did uninstall Evolution too after installing Ubuntu for the first time. I will reinstall it now and I will report back later. Thanks for the tip. :D

---

### Post by mjitkop on 2007-06-01
Update: it seems that reinstalling Evolution solved my problem. I restarted my PC several times since reinstalling it and no error message.

Thank you! :D

---

