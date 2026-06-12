---
title: "Cannot set niceness: Permission denied"
date: 2008-04-10
forum: General Help
---

### Post by SeanAloisi on 2008-04-10
Hi. I have been trying to run a niceness command on wine to make Starcraft and Steam run at a higher priority in Ubuntu 7.10 (Gutsy Gibbon). 

First I tried this:
nice -n -20 wine "C:\Program\ Files\Starcraft\Starcraft.exe"

This returned the following error:
 nice: cannot set niceness: Permission denied

So I then decided to run it with sudo, which returned this:
wine: /home/sean/.wine is not owned by you

I am curious if there is either a way to give myself permission to use the nice command, or if there is a way to give root shared ownership of my home directory. Thanks for any help.

---

### Post by bodhi.zazen on 2008-04-10
To set a nice value below 0 you need to use root powers ... ie sudo

---

### Post by SeanAloisi on 2008-04-10
Well is there anyway to give root ownership of my home folder if I am unable to set it as myself?

---

### Post by arvevans on 2008-04-10
This one is not an issue of who owns the folder.  It is because "nice" is a root command if you want to set nice values that would potentially harm the performance of other users or functions.  You will have to run it as root to make nice better than zero (i.e. a negative number).  The default is usually "10".

[INDENT]nice [-increment | -n increment ] command [argument ... ]
-increment | -n increment 	increment must be in the range 1-19; if not specified, an increment of 10 is assumed. An increment greater than 19 is equivalent to 19.

The super-user may run commands with priority higher than normal by using a negative increment such as -10. A negative increment assigned by an unprivileged user is ignored.[/INDENT]

Arv
_._

---

### Post by bodhi.zazen on 2008-04-10
> **SeanAloisi said:**
> Well is there anyway to give root ownership of my home folder if I am unable to set it as myself?

don't do that

start the process and use renice

I would step it down though, go to -5 , then -10 , then -15 , then -20

Just to make sure you do not introduce instability.

[http://www.cyberciti.biz/faq/howto-change-unix-linux-process-priority/](http://www.cyberciti.biz/faq/howto-change-unix-linux-process-priority/)

[http://www.hmug.org/man/8/renice.php](http://www.hmug.org/man/8/renice.php)

---

### Post by SeanAloisi on 2008-04-10
I am unable to run any nice commands under nice 0 as the regular user, but I am also unable to do it as root because root has no ownership of wine. How can I give it ownership?

---

### Post by bodhi.zazen on 2008-04-10
> **SeanAloisi said:**
> I am unable to run any nice commands under nice 0 as the regular user, but I am also unable to do it as root because root has no ownership of wine. How can I give it ownership?

You need to use the process ID

> bodhi@VirtualUbuntu:~$ ps aux | grep script

bodhi    **29239**  0.0  0.0   1756   488 pts/1    S    16:25   0:00 sh ./script
bodhi    29251  0.0  0.1   2972   752 pts/1    R+   16:25   0:00 grep script

bodhi@VirtualUbuntu: renice 0 **29239**                    
[color=green]29239: old priority 0, new priority 0[/color]

bodhi@VirtualUbuntu:~$ renice -1 **29239**                   
[color=red]renice: 29239: setpriority: Permission denied[/color]

bodhi@VirtualUbuntu:~/Test$ sudo renice -1 **29239**              
[sudo] password for bodhi:
[color=blue]29239: old priority 0, new priority -1[/color]

If you are having problems, could you please post the terminal output so we may see the commands and error message ?

---

