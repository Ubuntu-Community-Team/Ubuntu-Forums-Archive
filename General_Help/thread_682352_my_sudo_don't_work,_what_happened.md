---
title: "my sudo don't work, what happened?"
date: 2008-01-29
forum: General Help
---

### Post by chineseli on 2008-01-29
chineseli@chineseli-laptop:~$ sudo gedit /etc/fstab
sudo: must be setuid root 


what's wrong with it?  
I have just change my /usr mount place

---

### Post by dcstar on 2008-01-30
> **chineseli said:**
> chineseli@chineseli-laptop:~$ sudo gedit /etc/fstab
sudo: must be setuid root 


what's wrong with it?  
**I have just change my /usr mount place**

That is an extremely bad thing to do, /usr is a system directory with specific permissions that will break your system if you do not duplicate them exactly.

To answer your question, **you** just broke your system.

---

