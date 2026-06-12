---
title: "[SOLVED] cant move files to /usr"
date: 2007-07-13
forum: General Help
---

### Post by Archoniam on 2007-07-13
(I'm a dumb#$@.)
I cannot move files to /usr/bin/ . It just says I don't have permission. How the crap do i move files into /usr/bin or anywhere in /usr ? (Yes, i know how to become root in terminal. Just nowhere else XD)

---

### Post by bonzodog on 2007-07-13
how are you trying to move the files? In the command line, use 
```
sudo cp /path/to/my/file /usr/bin
```

If you want to do it graphically, press alt+F2 then type in 'gksudo nautilus'.

That should get you a file browser with root permissions.

---

### Post by iota on 2007-07-13
**Sudo cp <Location of files to copy> /usr/bin**

That should work, I think. Or you could use

**sudo chown <username> /usr/bin**

That should change the ownership to your good self, so you could stick shiz in there :)

---

### Post by aysiu on 2007-07-13
Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Archoniam on 2007-07-13
Okay thanks!!

---

### Post by aysiu on 2007-07-13
> **iota said:**
> 
**sudo chown <username> /usr/bin**

That should change the ownership to your good self, so you could stick shiz in there :) I would highly advise against ever changing ownership of a system directory. That would be a quick way to break your system.

---

### Post by Archoniam on 2007-07-13
Yep, i know. I did it the the non-graphical, sudo cp command way.:guitar:

---

### Post by iota on 2007-07-13
Ooh, sorry for suggesting that :(

Didn't realise it caused trouble. Looks like I'm using the interface way from now on :P

---

