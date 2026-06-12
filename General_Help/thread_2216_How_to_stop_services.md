---
title: "How to stop services?"
date: 2004-10-26
forum: General Help
---

### Post by kamstrup on 2004-10-26
During boot I see tons of services started that I really don't need. Like RAID managing and all kinds of stuff. Is there any easy way to disbale this?

Cheers!
kamstrup

---

### Post by normnmiles on 2004-10-26
update-rc.d can remove services from startup.  To use it find the name of the services you wish to disable, they are located under /etc/init.d/

then from a terminal use the command
```
$sudo update-rc.d -f [servicename] remove
```

---

### Post by luiska on 2004-10-28
Hi 

I used
 
apt-cache search runlevels 

to find a tool that will give me more a graphical representation of the services running. I installed one of them with apt-get install, there isnt very many and all of them seems to be console based.

Luiska

---

### Post by shufla on 2004-10-28
Hello,

[QUOTE=normnmiles]update-rc.d can remove services from startup.  To use it find the name of the services you wish to disable, they are located under /etc/init.d/

then from a terminal use the command
```
$sudo update-rc.d -f [servicename] remove
```[/QUOTE]

AFAIR there is little problem with update-rc.d After the package is updated symlinks are restored. I've found it in documentation for Debian somwhere (I was looking for it right now, cannot find :( ). The best solution is to put exit 0 on top of /etc/init.d/filename, below #!/bin/sh.

Not sure about:
Q1: Am I wrong about update-rc.d?
Q2: Is it specific to Debian or also to Ubuntu/Warty?

Best regards,
Lukasz Nowak

---

### Post by disposable on 2004-10-28
Go into /etc/rc2.d and mkdir stop, then mv the links for the services you want to stop there.

Edit: I haven't had any symlinks restored... yet.

---

### Post by kamstrup on 2004-11-04
Ok. I've used the update-rc.d thing and it seems to work. I would really like to see the runlevel editor from Gnome System Tools in universe/main though (maybe in Hoary?), but I can live without it.

Thanks for the help.

---

### Post by luiska on 2004-11-04
I am running Hoary on my laptop and after doing the apt-get upgrade thing this morning, havent done it since last friday, saw that there is a graphical runlevel editor now. Which is nice for the less adventurous, like me :)

Louis

---

