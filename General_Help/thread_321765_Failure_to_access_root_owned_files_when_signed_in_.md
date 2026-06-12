---
title: "Failure to access root owned files when signed in as root"
date: 2006-12-19
forum: General Help
---

### Post by theDentist on 2006-12-19
I am trying to access and read a file /etc/mysql/my.cnf  which is owned by root, Therefore, why  can't I open it when I am signed in as root!  I am still being refused access.  I thought computers were logical!   Have I missed something here.    ](*,) 


Peter

---

### Post by tszanon on 2006-12-19
The root account is locked by default, so you can't sign in as root unless you change it. So, I don't know what you're doing, but I think you're not signed as root. Anyway, let's see:

1. Typing this into the Terminal
```
cd /etc/mysql
ls -la my.cnf
```
should show something like this:
```
-rw-r--r-- root root my.cnf
```
Just trying to make sure that the permissions on the file are as expected (root can read/write, others can only read).

2. Typing
```
sudo gedit my.cnf
```
should bring up gEdit (the Text Editor) and the file my.cnf, ready for read/write. Typing just "gedit my.cnf" should bring up gEdit, but no writing allowed.

Did I misunderstand something?

---

### Post by TyphoonJoe on 2006-12-19
Do you have read permission to the file?  If not, run 

```
sudo chmod a+r filename
```

More on permissions here:
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

Computers are logical.  
The only time I have seen read failures when permissons are correct at the os-level have been when the filesystem is a samba mount that is not set up properly, or some other sort of external authenticaion issue.

---

