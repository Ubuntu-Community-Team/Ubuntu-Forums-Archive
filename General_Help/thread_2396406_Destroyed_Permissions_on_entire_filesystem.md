---
title: "Destroyed Permissions on entire filesystem"
date: 2018-07-15
forum: General Help
---

### Post by astarmathsandphysics on 2018-07-15
While trying to correct permissions on a drive I made a syntax error and destroyed the permissions on my entrire filesysterm.
Whenever I use sudo in a terminal I get this error 

sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set

I can't export databases or run websites on my server.
Unfortunately I havent seen that I dont have backups for one database and really need to get tht before I reinstall.
Is any recovery possible at all?
Any advice welcome.

---

### Post by Impavidus on 2018-07-15
When you destroy file permissions all over your system, recovery is hopeless. You should reinstall.

If your system is messed up so badly that you can't create backups, try using a live disk. You should be able to get a fully functional system and access all files on your hard drive to make backups.

---

### Post by QIII on 2018-07-15
You may ask:  "Isn't there some other way to fix it?"

The answer is "Yes", if you are intimately familiar with the default permissions for every file typcially installed and you have a week or two to correct them all.

Go with Impavidus' advice ... and add to it that you should do regular, versioned backups.  This is a painful lesson that many of us have learned over the years.

---

### Post by HermanAB on 2018-07-15
One way to fix it, is to create a virtual machine with the exact same version as the faulty server and then copying all the files over with rsync.  That of course assumes that your have a virtualizer that works...

---

