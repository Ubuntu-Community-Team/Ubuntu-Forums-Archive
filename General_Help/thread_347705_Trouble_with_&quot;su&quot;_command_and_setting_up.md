---
title: "Trouble with &quot;su&quot; command and setting up password"
date: 2007-01-27
forum: General Help
---

### Post by NuNn DaDdY on 2007-01-27
I just recently reinstalled Ubuntu but I need to know my "super user" (su) password when I type in the command.  I need to know this because I'm messing with my Grub menu.lst file so I can set the boot menu up how I want it and to change the countdown timer.  But I'm unsure on how to set up the super user password; would anyone know how to set this up so I can get the permissions to the files that I need to edit.

---

### Post by JamieC on 2007-01-27
Prefix commands you wish to run as root with sudo (unless they are graphical then you should use gksudo or kdesu respectively).

The password is the password of your account since you should have sudo privelleges.

---

### Post by taurus on 2007-01-27
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jwlockhart on 2008-01-06
well the easy way is as follows

*sudo passwd root*

and set a new root password then you can su over to root

---

### Post by bodhi.zazen on 2008-01-07
> **jwlockhart said:**
> well the easy way is as follows

*sudo passwd root*

and set a new root password then you can su over to root

Actually the easy way to do it is :

```
sudo -i
```

:twisted:

If you want to un-do a root password

sudo passwd root -l

That is a small L

---

