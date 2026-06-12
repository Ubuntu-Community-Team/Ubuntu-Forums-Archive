---
title: "Synaptic and other error - help"
date: 2004-11-19
forum: General Help
---

### Post by filattiera on 2004-11-19
Good morning,

onother big problem.
When I try to launch Synaptic from gnome console I have this error:

Failed to run /usr/sbin/synaptic as user root
Child terminated with 1 status

Now, this happens also with user/group management.
I think that this is a permission problem.

The /usr/sbin has user luca (my user of default) and group root.

Please, help me.

How do you can set for /usr/sbin 2 users permission?

Thanks.
Luke

---

### Post by WW on 2004-11-19
I don't know if this is your problem, but I can recreate that error message by entering the wrong password in the "Changing user" window that first pops up when I run Synaptic from the menu.  Don't forget that you must enter _your_ password (that is, luca's password) in this menu.

As you may know, ubuntu doesn't enable the root password by default, but even if you have enabled the root password, you must still enter your password (not root's) when you run Synaptic from the menu.

If that is what you are already doing, then I don't know what the problem is.  As you said, it could be a problem with the permissions.

I don't know why your /usr/sbin has user luca. On my system, both the user and group of /usr/sbin (and of everything in /usr/sbin) are root.

---

### Post by filattiera on 2004-11-19
[QUOTE=WW]I don't know if this is your problem, but I can recreate that error message by entering the wrong password in the "Changing user" window that first pops up when I run Synaptic from the menu.  Don't forget that you must enter _your_ password (that is, luca's password) in this menu.

As you may know, ubuntu doesn't enable the root password by default, but even if you have enabled the root password, you must still enter your password (not root's) when you run Synaptic from the menu.

If that is what you are already doing, then I don't know what the problem is.  As you said, it could be a problem with the permissions.

I don't know why your /usr/sbin has user luca. On my system, both the user and group of /usr/sbin (and of everything in /usr/sbin) are root.[/QUOTE]

Thanks.
The problem  was born after the Mysql installation.  I have done 
chown -R root:mysql /usr/sbin
chonw -R mysql:mysql /usr/sbin

After this, with my user luca (installing user) I don't more load synaptic and other programme (all theme that needed of password...).

I try to set 
chown -R root:root /usr/sbin 

The last thing to do before re-install all Ubuntu...

ciao.
Luke

 :?

---

