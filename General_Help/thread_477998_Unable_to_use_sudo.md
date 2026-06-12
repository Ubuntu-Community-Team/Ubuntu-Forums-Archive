---
title: "Unable to use sudo?"
date: 2007-06-18
forum: General Help
---

### Post by deinonychus75 on 2007-06-18
I don't understand.  I'm trying to remove an invalid driver, bcmwl5 for a Motorola wireless card.  In the terminal, when logged in as myself, if I type ndiswrapper -r bcmwl5 or bcmwl5.inf, I receive this message, "Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128 couldn't delete /etc/ndiswrapper/bcmwl5: Permission denied".  If I try it using the sudo command, it asks me for a password.  I was never asked to assign a password to the root so I don't have one or know what it is, and it doesn't seem to want to allow me to change the password.  If I enter through this, it returns to my username prompt.  If I check the list of drivers in ndiswrapper again using ndiswrapper -l, it says, "bcmwl5 : invalid driver!"  So, it doesn't remove it.

Do I need to find out exactly where the driver is and tell it?  Is that the problem?  I'm thoroughly confused.  Can someone please help?  Thank you.  I don't understand not being able to use the sudo command from my login, even though I'm in the admins group, and this whole deal with having a root user that you never get to choose a password for and can't log in as or change the password for has thrown me.

---

### Post by Amackera on 2007-06-18
This might not be your problem, but the sudo command works like this:

sudo ndiswrapper -r bcmwl5

You have to put sudo before the command. The command you're looking for is "su" which allows you to log in as root temporarily.

Your root password should just be your main account password, unless you've changed it.

---

### Post by fdrake on 2007-06-18
>  If I try it using the sudo command, it asks me for a password.  I was never asked to assign a password to the root so I don't have one or know what it is, and it doesn't seem to want to allow me to change the password. 
when you type sudo you have to use your password(not root's pass), the password you use when you login as a user in the session.

> 
Do I need to find out exactly where the driver is and tell it?  Is that the problem?  I'm thoroughly confused.  Can someone please help?  


like Amackera  said:

sudo ndiswrapper -r bcmwl5

You have to put sudo before the command. 

> 
I don't understand not being able to use the sudo command from my login, even though I'm in the admins group, and this whole deal with having a root user that you never get to choose a password for and can't log in as or change the password for has thrown me.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by deinonychus75 on 2007-06-18
Gotcha.  You two solved my problem.  Thanks!  :)  I tried typing my password before but must have typo'd it or something because it didn't want to work.  That's when I started wondering if I needed the root password.  This time I tried it, it worked!  Thank you!!!

---

