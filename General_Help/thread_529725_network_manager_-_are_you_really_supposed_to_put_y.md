---
title: "network manager - are you really supposed to put your password in every time!?"
date: 2007-08-19
forum: General Help
---

### Post by viciouslime on 2007-08-19
Do you really have to put your keyring password in EVERY time you login so that network manager can connect to the network!?

I'm sure this didn't used to be the case... I have found a number of very hackish hacks on the forums but are these really still necessary?

If so, which is the best one to use?

---

### Post by Gremlinzzz on 2007-08-19
go to /system/administration /login window /click security tab 
enable automatic login type in users name

---

### Post by viciouslime on 2007-08-20
> **Gremlinzzz said:**
> go to /system/administration /login window /click security tab 
enable automatic login type in users name

I don't think that solves the problem... that just stops them having to put their password in to login.

---

### Post by dAF2000 on 2007-08-20
There's a solution, because I've fixed it by editing a config file. But I forgot which file and what I did ;)
The solution is somewhere here written on the forum.

---

### Post by r_l on 2007-08-20
> **viciouslime said:**
> Do you really have to put your keyring password in EVERY time you login so that network manager can connect to the network!?

I'm sure this didn't used to be the case... I have found a number of very hackish hacks on the forums but are these really still necessary?

If so, which is the best one to use?

This one is easy and it worked for me:

[URL="http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/"]
http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/[/URL]

But the network manager has its own problem. The keyring now does it automatically, but sometimes the networkmanager still asked for the wireless password (not the keyring password). 

BTW, to change the default session password in the keyring, I simply deleted the default keyring in the keyring GUI.  It generates itself again upon reboot and I change the password (so it will be the same as my session password and the above hack would work).

---

