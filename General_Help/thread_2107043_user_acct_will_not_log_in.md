---
title: "user acct will not log in"
date: 2013-01-20
forum: General Help
---

### Post by badman35 on 2013-01-20
HI all I have Ubuntu 12.04.1 and after I installed a new vid card I can not log in to my user acct. could some one please help me with this. I have two other users on this pc but I am the admin for it and that user acct is the one I can not get into through the GUI. I have looked in the log files but I can not find what is causing this to do this.

---

### Post by badman35 on 2013-01-21
> **badman35 said:**
> HI all I have Ubuntu 12.04.1 and after I installed a new vid card I can not log in to my user acct. could some one please help me with this. I have two other users on this pc but I am the admin for it and that user acct is the one I can not get into through the GUI. I have looked in the log files but I can not find what is causing this to do this.
I have looked all through this forum for answers but none of them help at all. So I'll give more info on this thread.. I changed out my old nvidia gforce fx vid card with a zotac GT220 card. I upgraded the vid driver to current and uninstalled 173. Now most games work very nicely now. But my admin acct won't load on log in it just returns to the greeter screen. Pressing ctrl+alt+f1 will let me log in changing to gdm does not work for this one acct but as I stated before I can log on to it on command line. All the other user accts work great it does freeze up now and then when playing some games but a restart always brings it back and it works from then on. So could someone PLEASE give me some HELP!!!!!!! I need back into this acct.

---

### Post by steeldriver on 2013-01-21
Log in with the account at the Ctr-Alt-F1 virtual terminal

Now check the ownership and permissions on your account's home dir and Xauthority/ICEauthority files

```
ls -ld $HOME

ls -l $HOME/.{ICE,X}authority
```

---

### Post by badman35 on 2013-01-21
> **steeldriver said:**
> Log in with the account at the Ctr-Alt-F1 virtual terminal

Now check the ownership and permissions on your account's home dir and Xauthority/ICEauthority files

```
ls -ld $HOME

ls -l $HOME/.{ICE,X}authority
```
ok what am I looking for??? Oh and by the way thanks for your help..

---

### Post by badman35 on 2013-01-21
done checking and it looks like I still have ownership of the acct.

---

### Post by steeldriver on 2013-01-21
the directory needs to be owned / writable by you, and the authority files need to be owned by you and -rw------ (mode 600)

```
$ ls -ld $HOME
drwxr-xr-x 47 steeldriver steeldriver 4096 Jan 20 16:50 /home/steeldriver
$
$ ls -l $HOME/.{ICE,X}authority
-rw------- 1 steeldriver steeldriver 26124 Jan 20 16:50 /home/steeldriver/.ICEauthority
-rw------- 1 steeldriver steeldriver    53 Jan 20 16:50 /home/steeldriver/.Xauthority
$

```

---

### Post by badman35 on 2013-01-21
> **steeldriver said:**
> the directory needs to be owned / writable by you, and the authority files need to be owned by you and -rw------ (mode 600)

```
$ ls -ld $HOME
drwxr-xr-x 47 steeldriver steeldriver 4096 Jan 20 16:50 /home/steeldriver
$
$ ls -l $HOME/.{ICE,X}authority
-rw------- 1 steeldriver steeldriver 26124 Jan 20 16:50 /home/steeldriver/.ICEauthority
-rw------- 1 steeldriver steeldriver    53 Jan 20 16:50 /home/steeldriver/.Xauthority
$

```

Mine looks like your post but my user name instead.

---

### Post by badman35 on 2013-01-22
***bump****

---

