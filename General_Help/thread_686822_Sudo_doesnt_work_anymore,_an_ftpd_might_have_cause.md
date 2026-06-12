---
title: "Sudo doesnt work anymore, an ftpd might have caused it"
date: 2008-02-03
forum: General Help
---

### Post by ele_mugv on 2008-02-03
hello

Sudo doesnt work anymore. Whenever i use it nothing happens as u can see :

```


ele-mugv@ele-Open-source-box:/etc$ sudo gedit usplash.conf 
[sudo] password for ele-mugv:
ele-mugv@ele-Open-source-box:/etc$ 

```
 I have a feeling it has something to do with pure ftpd which i uninstalled to install proftpd. Please help with instructions on how to get it working.. Im still a newbie at ubuntu ;)

---

### Post by ele_mugv on 2008-02-03
sudo nano doesnt work as well so its not a gedit thing by the way :(

---

### Post by bodhi.zazen on 2008-02-03
I would guess it is because you are not in the admin group.

[http://ubuntuforums.org/showpost.php?p=3282837&postcount=4](http://ubuntuforums.org/showpost.php?p=3282837&postcount=4)

Also, for graphical apps, use gksu, kdesu on KDE:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by z-itou16 on 2008-02-08
hi everyone.
i am not an expert but i am willing to learn more and more each time. i will assume you have gedit install properly as well as nano, so i wont touch that. 

please i will like you to type this in the terminal:
> echo $PATH

must likely you should get /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games. what i am looking is if you get at least /usr/bin for now.

please let me know. i will try to help the most i can. when i see your reply i may get the idea what you have and how can we solve it. 

thanks everyone

---

