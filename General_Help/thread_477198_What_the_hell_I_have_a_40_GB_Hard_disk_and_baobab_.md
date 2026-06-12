---
title: "What the hell? I have a 40 GB Hard disk and baobab says i have 63 GB Free?????"
date: 2007-06-18
forum: General Help
---

### Post by mthakur2006 on 2007-06-18
How does this work? is this a rootkit or something?

---

### Post by Brucevdk on 2007-06-18
Maybe this is because baobab goes into */media* and includes the free/used space for any of your mounts too. Do you have anything mounted that could have 23GB free space? Perhaps check out the filesystem tab in *gnome-system-monitor* and add up the numbers.

---

### Post by mthakur2006 on 2007-06-18
i have a separate 8 GB partition for windows and the rest 32 GB is for ubuntu, adds upto 40 GB. How the holy god is baobab saying i have 63 GB?

---

### Post by Rui Pais on 2007-06-18
Hi.
File a bug report. 

baobab is a very strange (buggy?) thing. It calculates space, deliberately it seems,  in a very weird manner... 


I completely give up on that and use filelight (from kde, that made me install parts of kde that i don't need but at least work i a way i understand)

---

### Post by mthakur2006 on 2007-06-18
> **Rui Pais said:**
> Hi.
File a bug report. 

baobab is a very strange (buggy?) thing. It calculates space, deliberately it seems,  in a very weird manner... 


I completely give up on that and use filelight (from kde, that made me install parts of kde that i don't need but at least work i a way i understand)

cool, but how do you file a bug report? sorry about the noob question but in my two year stint with ubuntu, i haven't had a single problem apart from self-explanatory ones. :D

---

### Post by Rui Pais on 2007-06-18
> **mthakur2006 said:**
> cool, but how do you file a bug report? sorry about the noob question but in my two year stint with ubuntu, i haven't had a single problem apart from self-explanatory ones. :D

Oops. No sorry me, i'm assumed you know how :)

It's here:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

search for already filled bugs for baobab
create a new if you find nothing of the kind (doubt it) or confirm you case on an existing one.

Good luck.

---

### Post by mthakur2006 on 2007-06-19
kk thank you so much, now i can help ubuntu become better.
thanks.

---

