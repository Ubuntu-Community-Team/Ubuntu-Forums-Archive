---
title: "Root access help"
date: 2006-11-16
forum: General Help
---

### Post by anarky on 2006-11-16
Elo everyone, i recently made the switch to linux and i love it so far. Just one problem, i cant install some of the things that i want to because i cant access the root account :-k  When i goto switch users and log into the root account i get the error of "The root account cannot be accessed from this location." ](*,) I am running 6.10 edge :) thanks for any help.

---

### Post by CatKiller on 2006-11-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by computx on 2006-11-16
The root account for ubuntu is disabled by default. Instead type sudo <command> then enter **your** password when prompted.

You can also sudo su and enter your password to get a root command prompt.

Finally, if you really want to log in as root. (bad idea) You can "sudo su" then "passwd root" and enter a password after which root logins will no longer be disabled.

---

### Post by anarky on 2006-11-16
erm... i get stuck on the switch user :X it asks for pass but i cant type in the pass :X sory never used linux before :X

---

### Post by taurus on 2006-11-16
When you type in the password, you won't see any echo so don't worry about it.  It's normal.  Just type it in and hit enter...

---

### Post by PrinceArithon on 2006-11-16
To be honest with you, the best way to install anything is using the sudo command.  Something like: 

sudo apt-get install skype


It's much safer than being in root.  Try it and everything should install

---

### Post by anarky on 2006-11-16
> **taurus said:**
> When you type in the password, you won't see any echo so don't worry about it.  It's normal.  Just type it in and hit enter...
ohhh i didnt know that ><
anyways off to bed for now ill try it 2mrrw :) thanks for the help everyone :D

---

### Post by aysiu on 2006-11-16
> **taurus said:**
> When you type in the password, you won't see any echo so don't worry about it.  It's normal.  Just type it in and hit enter...
This problem keeps coming up over and over again, but the devs rejected my bug report on it.

More details here:
[Feedback on entering password in the terminal?](http://ubuntuforums.org/showthread.php?t=214393&highlight=password+terminal+feedback)

Actual rejected bug report here:
[https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914](https://launchpad.net/distros/ubuntu/+source/gnome-terminal/+bug/52914)

---

