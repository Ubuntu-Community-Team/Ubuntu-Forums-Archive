---
title: "file permission question"
date: 2008-05-23
forum: General Help
---

### Post by fouadk on 2008-05-23
hi everyone....

the scenario is the following...we use a windows active directory with around 3000 users....those users have files and documents and stuff that need to be placed on a Linux machine in order to avoid viruses and nasty stuff....

the way i thought about it is to create a folder named "Files" under / and then under this folder create a folder named after each windows active directory user and give the user read and write permission to that user....

is that doable ???

please help...

thanks in advance :D

---

### Post by scorp123 on 2008-05-23
> **fouadk said:**
>  those users have files and documents and stuff that need to be placed on a Linux machine in order to avoid viruses and nasty stuff....  If those files can still be accessed by (potentially infected) Windows desktops then placing them onto a Linux server offers *NO* protection against viruses!

The only thing protected here is the Linux server itself, the virus can't hurt it. And you could install a virus scanner on this server so it prevents Windows viruses from spreading via the file shares. But still: for as long as you have Windows desktops in your equation you are susceptible to losing files to viruses.

> **fouadk said:**
>  the way i thought about it is to create a folder named "Files" under / and then under this folder create a folder named after each windows active directory user and give the user read and write permission to that user....  Why reinvent the wheel and the fire? Why not just move their home directories onto the Linux server? Voila, done.

And you may wish to read this thread:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

---

### Post by fouadk on 2008-05-23
thank you for your reply....

considering the virus thing...my primarily purpose is to protect the server not the desktops....

i didnt understand the second part of your post...the one related to moving their home directories....
those are active directory users....its windows....where would a home directory be located ????
if you could provide more help with that i would be grateful....

---

