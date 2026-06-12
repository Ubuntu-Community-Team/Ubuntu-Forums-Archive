---
title: "Changing permissions"
date: 2007-05-07
forum: General Help
---

### Post by gwatts on 2007-05-07
Using Ubuntu 7.04

There are 3 listing in home file:
1kk (My User name)
2MyFiles
3 samba
Both samba and MyFiles are empty, are owned  by root and I have no permissions.
Samba allows my XP computers to access the Ubuntu computer.

I believe that I changed MyFiles using chmod a+rw MyFiles, from something to :
drwxrwxrwx   3 kk   root  4096 2007-05-07 07:37 MyFiles 
Anyway that is how it lists now.

Doesn't this indicate that user kk can read and write too MyFiles?
I am the only owner, user and group.

What should I do to control or change these permissions so that I can read write and access.

Thank you.

---

### Post by lynxus on 2007-05-07
Root up or run  CHown via sudo to change the owner.

---

### Post by gwatts on 2007-05-07
Done.
Thank you.

---

