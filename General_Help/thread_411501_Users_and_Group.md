---
title: "Users and Group"
date: 2007-04-16
forum: General Help
---

### Post by Leebo on 2007-04-16
Hi all was wondering if this was a bug or what :P

I was trying to install crossover and i get an error saying my home doesnt belong to me and that i needed to point $HOME to my home directory and try again. When i check the users/groups under ubuntu low and behold my user is not listed...so what gives? heh everything works properly....my home directory is there but I dont know why it is not showing it doesnt belong to me. I tried creating a new user to add me to the users and group...but it says that user already exists. So now im stumped heh.

Any help would be apprciated, and i'm still learning the "linux ropes" so be please be gentle

Thanks,

Leebo

---

### Post by rmemm on 2007-04-17
You could do a little exploring in some of the system config files in /etc.

Users are listed in /etc/passwd

Groups are in /etc/group

Your user and group setup should be there if your defined on the system.

Rob

---

