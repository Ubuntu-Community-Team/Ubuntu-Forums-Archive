---
title: "Can't update"
date: 2007-03-26
forum: General Help
---

### Post by nickd916 on 2007-03-26
When I clcik to install updates i get an error message.  It says " E:dpkg was interrupted, you must manually run 'dpkg - - configure -a' to correct the problem"   I am new to Ubuntu

---

### Post by nickd916 on 2007-03-26
When I clcik to install updates i get an error message.  It says " E:dpkg was interrupted, you must manually run 'dpkg - - configure -a' to correct the problem"   I am new to Ubuntu..Can someone please explain in English?

---

### Post by dcstar on 2007-03-26
> **nickd916 said:**
> When I clcik to install updates i get an error message.  It says " E:dpkg was interrupted, you must manually run 'dpkg - - configure -a' to correct the problem"   I am new to Ubuntu

Open a Terminal screen, then type:
```
sudo dpkg -- configure -a
```
and enter your password when prompted.

---

### Post by will_in_wi on 2007-03-26
Open a terminal (Applications -> Accessories -> Terminal) and type:
```
sudo dpkg - - configure -a
```
Hit Enter and then when it is done type exit and hit enter. This should fix the system.

---

### Post by nickd916 on 2007-03-26
That seems to have done the trick.  Thanks.

---

### Post by bthom52 on 2007-03-31
David--I saw your post to nickd916.  I'm having the same error message when I try to update Xubuntu.  I used the command you provided, but can't get it to work.  I'm a novice at Linux.

---

