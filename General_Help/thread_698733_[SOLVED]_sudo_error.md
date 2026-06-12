---
title: "[SOLVED] sudo error"
date: 2008-02-16
forum: General Help
---

### Post by soxs on 2008-02-16
Whatever command I try with sudo, I get following error:
```
x@x:/usr/bin$ sudo *csome_command*
sudo: must be setuid root
```

I thought it may be caused by having edited some rights in /usr/bin so I posted the rwx modes aswell:
```
x@x:/usr/bin$ ls -Al |grep sudo
lrwxrwxrwx 1 root   root          4 2008-02-16 19:47 gksudo -> gksu
-rwxr-xr-x 2 root   root     122528 2008-01-22 20:59 sudo
-rwxr-xr-x 2 root   root     122528 2008-01-22 20:59 sudoedit
```

```
x@x:/usr/bin$ sudoedit
sudoedit: must be setuid root
```

May sombody give me a hint, what setuid is and what I can do to change it and fix my problem.
Note: gksu does not give an error nor does any gtk window show.

---

### Post by nemilar on 2008-02-16
try this:

```
chmod +s /usr/bin/sudo
```

I'm guessing at some point you 'chmod 755 /usr/bin/sudo' 

Oh... uhh.  You're gonna have to be root to do that.  Hope you set a root password and you can use su!

---

### Post by soxs on 2008-02-16
yes, setting root passwd is the first thing I do when I#ve done a fresh install^^ I must be really lucky thx

EDIT: ok, seems to work, THX A LOT

---

