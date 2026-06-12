---
title: "NEWB ALERT!! Error message HELP"
date: 2008-04-17
forum: General Help
---

### Post by coachmad on 2008-04-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open()failed,please report

When I try to launch synaptic package manager

Please help thanks ahead of time
windows user attempting to go to the dark side

---

### Post by sekinto on 2008-04-17
You should do what it says. Try running
```
dpkg --configure -a
```
in a terminal.

Edit:
You may have to do
```
sudo dpkg --configure -a
```
I'm not sure what permissions dpkg requires.

---

### Post by coachmad on 2008-04-17
ok i did... got this
what is superuser???


dpkg: requested operation requires superuser privilege

---

### Post by ad_267 on 2008-04-17
To get to a terminal go Applications -> Accessories -> Terminal then type that command. sudo is used to give you root access (like administrator privileges in windows) and will require you to enter your password

Edit: you need the sudo in front

---

### Post by rune0077 on 2008-04-17
> **coachmad said:**
> ok i did... got this
what is superuser???


dpkg: requested operation requires superuser privilege

It means you need to use the second code (type "sudo" in front of the command).

---

### Post by sekinto on 2008-04-17
> **coachmad said:**
> ok i did... got this
what is superuser???


dpkg: requested operation requires superuser privilege


Put a sudo before the command then.

---

### Post by coachmad on 2008-04-17
hotdamn!!! cheers EVERYONE! sudo did the trick 

wow what great support better than the EVIL EMPIRE SOFTIES!!
:lolflag:

---

