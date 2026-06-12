---
title: "What is the trick of that admin group in Ubuntu?"
date: 2007-03-12
forum: General Help
---

### Post by rammel on 2007-03-12
Hi,

together with my co-workers I develop an application that creates threads with realtime policy (FIFO) so it needs root privileges to run.
They all use ubuntu while I'm sticking to gentoo. Under ubuntu they are able to run our application with their user account created at installation time (that one that is part of group admin).
Under gentoo I've to run it as root ore use sudo.

My Question is:
How can I emulate this ubuntu admin group under other linux distributions? I could find out what ("trick") that admin group does, I scanned all files (including that under dev and proc), but none does belong to group "admin".
Do you have any tips?

Thanks for your help!

---

### Post by az on 2007-03-12
Ubuntu uses sudo and dissables the root account by default.  The first user created is given root privileges through sudo.  That's it.

---

### Post by Ramses de Norre on 2007-03-12
The trick is including following line in /etc/sudoers: ```
%admin  ALL=(ALL) ALL
```
The '%' is because you're giving permissions to a group, all members from the admin group get full root access from this line. You can put any other group instead of admin there too.

---

### Post by rammel on 2007-03-12
thanks, but as i said, they are able to run that app _without_ sudo, so it's no sudoers-thing.

i experimented a bit and found out now it hast nothing to do with the admin group, too. an ubuntu account removed from it is still able to execute our app. it seems it has to do with linux kernel capabilities, but I read the first time in my life about it 5 minits ago, so I could be wrong ;)

---

### Post by zvacet on 2007-03-12
Naturaly you can run apps without be member of admin,but you can not install or do anything else wich include using sudo.

---

### Post by rammel on 2007-03-12
i used lcap utility now to check the difference in the set of kernel capabilities enabled under gentoo and ubuntu: no difference, so it has to be something else.

Why is it possible to create threads with real-time-policy (FIFO) under ubuntu as user but not under gentoo? my head is smoking...

---

### Post by rammel on 2007-03-12
I solved it: under gentoo I had to manually install the kernel module realtime and load it with 
#modprobe realtime any=1
in ubuntu it is already patched in the kerneltree.

---

