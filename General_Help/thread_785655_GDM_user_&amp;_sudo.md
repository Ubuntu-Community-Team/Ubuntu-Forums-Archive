---
title: "GDM user &amp; sudo"
date: 2008-05-07
forum: General Help
---

### Post by Beginner24 on 2008-05-07
Hello!

I have upgraded Ubuntu version 8.04 which is upgraded from v 7.10.

Since I have upgraded to this version, there are some problems with system administration. 

When I turn on my computer, there is a following attention: **The GDM user 'gdm'does not exist. Please correct GDM configuration and restart GDM** With command **startx ** I got back graphical enviroment. I've got information in other threads, how to fix it, but there is the next problem - when i type sudo commands in terminal, it says: ** unable to resolve host Grausts**.   

I am thinking to reinstall Ubuntu, but I can not make a home folder partition, because sudo commands doesn't work.

P.S.

Sorry for my English. I am from non-English country. ;)

---

### Post by prshah on 2008-05-07
> **Beginner24 said:**
> but there is the next problem - when i type sudo commands in terminal, it says: ** unable to resolve host Grausts**.   


To clear your "next" problem, (don't know anything about the first), open a terminal (Applications-Accessories-Terminal) then give the command ```
hostname
``` Note the name shown and then give the command ```
gksudo
```

A window will open up, in the command box, type ```
gedit /etc/hosts
``` and choose "user" as "root", then OK/Enter. A new window will open up, look for the line beginning with ```
127.0.0.1 
``` and change the word following that number to the same as in the hostname command above Note that case (UPPER/lower/Mixed) is important. Then save and quit.

Now your sudo should be working fine.

---

### Post by Beginner24 on 2008-05-07
Thanks for that!   But there follows another problem. I think it is similar with GDM user problem.    I have done that, what you said, but in a new window was said, that user root does not exist, and so I need sudo commands to fix root user problem.

---

### Post by prshah on 2008-05-07
> **Beginner24 said:**
>  that user root does not exist, and so I need sudo commands to fix root user problem.

OK, if you go to recovery mode (when booting, in the GRUB menu, select recovery mode) you can have root access without using sudo. In such case, the command will become```
nano /etc/hosts
```

But considering this error, I believe you will be better off reinstalling; something seems to have gone seriously wrong. No harm in trying the recovery console edit of /etc/hosts first, though.

---

### Post by Beginner24 on 2008-05-12
I've tried to reinstall the Ubuntu.  I tried to Boot in trough Live CD, but anything doesn't happened. There is no difference, when I boot in using live CD or HDD - it always boots using HDD and existing Ubuntu. 

I have no ideas whats the matter! :confused:

---

### Post by prshah on 2008-05-13
> **Beginner24 said:**
> when I boot in using live CD or HDD - it always boots using HDD and existing Ubuntu. 


Change your boot devices order in the BIOS (keep tapping, alternately, the DEL key and the F2 key).

Set it to boot first from CDROM, then from Hard Disk.

For more details, post a screenshot (with a digital camera) of your BIOS screen.

---

### Post by Beginner24 on 2008-05-14
It's all right now!   The Live CD was broken, now I reinstalled Ubuntu v7.10. 

Thanks for help! ;)

---

