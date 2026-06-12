---
title: "Desktop background problem."
date: 2015-02-08
forum: General Help
---

### Post by dtree46 on 2015-02-08
SOLVED                   When right clicking on the desktop to change background settings, the attached gui opens instead of the one that should.
How is this solved?

dlw

---

### Post by mc4man on 2015-02-08
probably would be useful to provide some info - this will suffice
```

lsb_release -a && echo $DESKTOP_SESSION
```

---

### Post by dtree46 on 2015-02-09
Thanks for replying.

lsb_release -a && echo $DESKTOP_SESSION
dlw@dlw-HP:~$ lsb_release -a && echo $DESKTOP_SESSION
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
ubuntu
dlw@dlw-HP:~$

---

### Post by mc4man on 2015-02-09
Try this, if already installed it will say so, if not then go ahead & allow install. Then log out/in & see if any better
```
sudo apt-get install unity-settings-daemon ubuntu-settings
```

---

### Post by dtree46 on 2015-02-09
dlw@dlw-HP:~$ sudo apt-get install unity-settings-daemon ubuntu-settings
[sudo] password for dlw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-settings is already the newest version.
unity-settings-daemon is already the newest version.

---

### Post by mc4man on 2015-02-09
For starters try to open a couple of the missing panels in a terminal - 
unity-control-center appearance
unity-control-center info
unity-control-center display
unity-control-center user-accounts
do any of them open or what does the terminal say? (do one at a time..

---

### Post by mc4man on 2015-02-09
> **mc4man said:**
> Try this, if already installed it will say so, if not then go ahead & allow install. Then log out/in & see if any better
```
sudo apt-get install unity-settings-daemon ubuntu-settings
```
oops - meant unity-control-center, not unity-settings-daemon. so ck.
```
sudo apt-get install unity-control-center

```

---

### Post by dtree46 on 2015-02-09
dlw@dlw-HP:~$ unity-control-center appearance
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt-get install unity-control-center
dlw@dlw-HP:~$ unity-control-center info
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt-get install unity-control-center
dlw@dlw-HP:~$ unity-control-center display
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt-get install unity-control-center
dlw@dlw-HP:~$ unity-control-center user-accounts
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt-get install unity-control-center
dlw@dlw-HP:~$ 
dlw@dlw-HP:~$ unity-control-center
The program 'unity-control-center' is currently not installed. You can install it by typing:
sudo apt-get install unity-control-center
dlw@dlw-HP:~$ sudo apt-get install unity-control-center

Rebooting now.

---

### Post by dtree46 on 2015-02-09
That worked. Thank you.

dlw

---

